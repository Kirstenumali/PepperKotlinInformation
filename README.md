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

The local is inside Locale
``` bash
override fun onRobotFocusGained(qiContext: QiContext) {
        this.qiContext = qiContext
        val topic: Topic = TopicBuilder.with(qiContext)
            .withResource(R.raw.main_ar)
            .build()
        val locale: Locale = Locale(Language.ARABIC, Region.SAUDI_ARABIA)
        sayText("يرجى اختيار الاغنية", locale)
        
        val qiChatbot: QiChatbot = QiChatbotBuilder
            .with(qiContext)
            .withTopic(topic)
            .withLocale(locale)
            .build()
        val executors = HashMap<String, QiChatExecutor>()

        executors["Handshake"] = Handshake(qiContext)
        qiChatbot.executors = executors
        val chatbots  = mutableListOf<Chatbot>()
        chatbots.add(qiChatbot)
        val chat: Chat = ChatBuilder.with(qiContext).withChatbot(qiChatbot).withLocale(locale).build()
        chat.async().run()
        
        qiChatbot.addOnBookmarkReachedListener {
            when (it.name) {
                "shark" -> {
                    val intent = Intent(this, ArDanceActivity::class.java)
                    intent.putExtra("videoName", "video_1")
                    startActivity(intent)
                }
                "jump" -> {
                    val intent = Intent(this, ArDanceActivity::class.java)
                    intent.putExtra("videoName", "video_2")
                    startActivity(intent)
                }
                "count" -> {
                    val intent = Intent(this, ArDanceActivity::class.java)
                    intent.putExtra("videoName", "video_3")
                    startActivity(intent)
                }
                "bus" -> {
                    val intent = Intent(this, ArDanceActivity::class.java)
                    intent.putExtra("videoName", "video_4")
                    startActivity(intent)
                }
                "fruit" -> {
                    val intent = Intent(this, ArDanceActivity::class.java)
                    intent.putExtra("videoName", "main_video")
                    startActivity(intent)
                }
                "back" -> {
                    startActivity(Intent(this, SelectLanguageActivity::class.java))
                }
            }
        }
        touchHead(this.qiContext!!)
    }
```

This is English
``` bash
override fun onRobotFocusGained(qiContext: QiContext) {
        this.qiContext = qiContext
        sayText("Okey! Please choose which dance you want me to perform")

        val topic: Topic = TopicBuilder.with(qiContext)
            .withResource(R.raw.main)
            .build()

        val qiChatbot: QiChatbot = QiChatbotBuilder.with(qiContext).withTopic(topic).build()

        val executors = HashMap<String, QiChatExecutor>()
        executors["Handshake"] = Handshake(qiContext)

        qiChatbot.executors = executors
        val chatbots  = mutableListOf<Chatbot>()
        chatbots.add(qiChatbot)

        val chat: Chat = ChatBuilder.with(qiContext).withChatbot(qiChatbot).build()
        chat.async().run()

        qiChatbot.addOnBookmarkReachedListener {
            when (it.name) {
                "shark" -> {
                    val intent = Intent(this, DanceActivity::class.java)
                    intent.putExtra("videoName", "video_1")
                    startActivity(intent)
                }
                "jump" -> {
                    val intent = Intent(this, DanceActivity::class.java)
                    intent.putExtra("videoName", "video_2")
                    startActivity(intent)
                }
                "count" -> {
                    val intent = Intent(this, DanceActivity::class.java)
                    intent.putExtra("videoName", "video_3")
                    startActivity(intent)
                }
                "bus" -> {
                    val intent = Intent(this, DanceActivity::class.java)
                    intent.putExtra("videoName", "video_4")
                    startActivity(intent)
                }
                "fruit" -> {
                    val intent = Intent(this, DanceActivity::class.java)
                    intent.putExtra("videoName", "main_video")
                    startActivity(intent)
                }
                "back" -> {
                    startActivity(Intent(this, SelectLanguageActivity::class.java))
                }
            }
        }
        touchHead(this.qiContext!!)
    }
```





for production use for human detection







