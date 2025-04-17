# Pepper_Kotlin_Information



The method named **onRobotFocusGained is use for not to run in other activities**
``` bash
override fun onRobotFocusGained(qiContext: QiContext) {
        this.qiContext = qiContext
    }
```

Gpt prompt
``` bash
destroy the handler if its totally finish this app.
```
This is a handler destroy
``` bash
   private lateinit var handler: Handler
    private lateinit var runnable: Runnable
```
``` bash
 handler = Handler(Looper.getMainLooper())
 runnable = Runnable {
            val intent = Intent(this@1Activity, 2Activity::class.java)
            startActivity(intent)
            finish()
 }
 handler.postDelayed(runnable, 120000)
```

``` bash
handler.removeCallbacks(runnable) // onDestroy
```










``` bash
package com.softbankrobotics.peppergamepadsample

import android.content.Intent
import android.os.Bundle
import android.os.Handler
import android.os.Looper
import com.aldebaran.qi.sdk.QiContext
import com.aldebaran.qi.sdk.QiSDK
import com.aldebaran.qi.sdk.RobotLifecycleCallbacks
import com.aldebaran.qi.sdk.`object`.conversation.*
import com.aldebaran.qi.sdk.`object`.humanawareness.HumanAwareness
import com.aldebaran.qi.sdk.`object`.touch.TouchSensor
import com.aldebaran.qi.sdk.builder.*
import com.aldebaran.qi.sdk.design.activity.RobotActivity
import com.aldebaran.qi.sdk.design.activity.conversationstatus.SpeechBarDisplayStrategy

class Id42bDnvActivity : RobotActivity(), RobotLifecycleCallbacks {
    companion object {
        const val TAG = "Id 42b Dnv Activity" }
    private var qiContext: QiContext? = null
    private var chat: Chat? = null
    private var headTouchSensor: TouchSensor? = null
    private var humanAwareness: HumanAwareness? = null
    private var greetingState: Boolean = true

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_id42b_dnv)
        QiSDK.register(this, this)
        setSpeechBarDisplayStrategy(SpeechBarDisplayStrategy.IMMERSIVE)
        greetingState = intent.getBooleanExtra("greetingState", false)
        Handler(Looper.getMainLooper()).postDelayed({
            startActivity(Intent(this, Id42bbDnvActivity::class.java))
            finish()
        }, 15000)
    }

    private fun sayText(text: String) {
        val say = SayBuilder.with(qiContext)
            .withText(text)
            .build()
        say.run()
    }

    override fun onRobotFocusGained(qiContext: QiContext) {
        this.qiContext = qiContext
        sayText("Shortly, I will open the registration form for each visitor to fill up, once you fill your form please proceed to reception desk to collect your id badge. which is for identification purposes only, it must be clearly displayed while in the office")
        humanAwareness = qiContext.humanAwareness }
    override fun onRobotFocusLost() {
        chat?.removeAllOnStartedListeners()
        headTouchSensor?.removeAllOnStateChangedListeners()
        qiContext = null }
    override fun onRobotFocusRefused(reason: String?) {}

    override fun onDestroy() {
        super.onDestroy()
        QiSDK.unregister(this, this)
        greetingState = false
        headTouchSensor?.removeAllOnStateChangedListeners()
        headTouchSensor = null
        qiContext = null
        chat?.removeAllOnStartedListeners()
        chat = null
        humanAwareness = null
    }

    internal inner class Handshake(qiContext: QiContext) : BaseQiChatExecutor(qiContext) {

        override fun runWith(params: List<String>) {
            animate(qiContext) }
        override fun stop() {}
        private fun animate(qiContext: QiContext) {
            val animation = AnimationBuilder.with(qiContext)
                .withResources(R.raw.handshake)
                .build()
            val animate = AnimateBuilder.with(qiContext)
                .withAnimation(animation)
                .build()
            animate.run()
        }
    }
}
```
