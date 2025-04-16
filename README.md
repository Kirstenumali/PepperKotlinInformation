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

