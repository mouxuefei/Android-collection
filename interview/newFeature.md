<p><span style="font-size:14px;color:#9999ff;"><span style="font-weight:bold;">Android 5.0行为变更</span></span></p>
<p><span style="font-size:14px;">API级别：21</span></p>
<p><span style="font-size:14px;color:#f00;">1. Android Runtime(ART)</span></p>

<p><span style="font-size:14px;">大多数 Android 应用无需任何更改就可以在 ART 下工作。不过，部分适合 Dalvik 的技术并不适用于 ART。如需了解有关最重要问题的信息，请参阅在 Android Runtime (ART) 上验证应用行为。如存在以下情况，应特别注意：</span></p>

<p><span style="font-size:14px;">您的应用使用<span> </span><a href="https://www.2cto.com/kf/ware/Java/" rel="nofollow" class="keylink">Java</a><span> </span>原生接口 (JNI) 运行 C/C++ 代码。</span></p>

<p><span style="font-size:14px;">您使用生成非标准代码的开发工具(例如，一些代码混淆工具)。</span></p>

<p><span style="font-size:14px;">您使用与压缩垃圾回收不兼容的技术</span></p>

<p><span style="font-size:14px;color:#f00;">2. 声音和振动</span></p>

<p><span style="font-size:14px;">如果您当前使用 Ringtone、MediaPlayer 或 Vibrator 类向通知中添加声音和振动，则移除此代码，以便系统可以在“优先”模式中正确显示通知。取而代之的是，使用 Notification.Builder 方法添加声音和振动。</span></p>

<p><span style="font-size:14px;">将设备设为 RINGER_MODE_SILENT 可使设备进入新的优先模式。如果您将设备设为 RINGER_MODE_NORMAL 或 RINGER_MODE_VIBRATE，则设备将退出优先模式。</span></p>

<p><span style="font-size:14px;">以前，Android 使用 STREAM_MUSIC 作为主流式传输来控制平板电脑设备上的音量。在 Android 5.0 中，手机和平板电脑设备的主音量流式传输现已合并，由 STREAM_RING 或 STREAM_NOTIFICATION 进行控制。</span></p>

<p><span style="font-size:16px;color:#f00;">3. 锁定屏幕可见性</span></p>

<p><span style="font-size:14px;">默认情况下，在 Android 5.0 中，通知现在显示在用户的锁定屏幕上。用户可以选择保护敏感信息不被公开，在此情况下，系统会自动删减通知显示的文本。要自定义此删减的通知，请使用 setPublicVersion()。</span></p>
<p><span style="font-size:14px;">如果通知不包含个人信息，或者您想允许媒体播放控件显示在通知上，则调用 setVisibility() 方法并将通知的可见性级别设为 VISIBILITY_PUBLIC。</span></p>
<p><span style="font-size:14px;color:#f00;">4. 浮动通知</span></p>
<p><span style="font-size:14px;">现在，当设备处于活动状态时(即，设备未锁定且其屏幕已打开)，通知可以显示在小型浮动窗口中(也称为“浮动通知”)。这些通知看上去类似于精简版的通知，只是浮动通知还显示操作按钮。用户可以在不离开当前应用的情况下处理或清除浮动通知。</span></p>
<p><span style="font-size:14px;">可能触发浮动通知的条件示例包括：</span></p>
<p><span style="font-size:14px;">用户的 Activity 处于全屏模式中(应用使用 fullScreenIntent)</span></p>
<p><span style="font-size:14px;">通知具有较高的优先级并使用铃声或振动</span></p>
<p><span style="font-size:14px;">如果您的应用在以上任何情形下实现通知，请确保系统正确显示浮动通知。</span></p>
<p><span style="font-size:14px;color:#f00;">5. getRecentTasks()</span></p>
<p><span style="font-size:14px;">为提升用户隐私的安全性，现已弃用 ActivityManager.getRecentTasks() 方法。对于向后兼容性，此方法仍会返回它的一小部分数据，包括调用应用自己的任务和可能的一些其他非敏感任务(如首页)。如果您的应用使用此方法检索它自己的任务，则改用 getAppTasks() 检索该信息。</span></p>
<p><span style="font-size:14px;color:#f00;">6. 绑定到服务</span></p>
<p><span style="font-size:14px;">Context.bindService() 方法现在需要显式 Intent，如果提供隐式 intent，将引发异常。为确保应用的安全性，请使用显式 intent 启动或绑定 Service，且不要为服务声明 intent 过滤器。</span></p>
<p><span style="font-size:14px;color:#f00;">7. webview</span></p>
<p><span style="font-size:14px;">Android 5.0 更改了应用的默认行为。</span></p>
<p><span style="font-size:14px;">如果您的应用是面向 API 级别 21 或更高级别：</span></p>
<p><span style="font-size:14px;">默认情况下，系统会阻止混合内容和第三方 Cookie。要允许混合内容和第三方 Cookie，请分别使用 setMixedContentMode() 和 setAcceptThirdPartyCookies() 方法。</span></p>
<p><span style="font-size:14px;">系统现在可以智能地选择要绘制的 HTML 文档部分。这个新的默认行为有助于减少内存占用和提升性能。如果您要一次渲染整个文档，可通过调用 enableSlowWholeDocumentDraw() 停用此优化。</span></p>
<p><span style="font-size:14px;">如果您的应用是面向低于 21 的 API 级别：系统允许混合内容和第三方 Cookie，并始终一次渲染整个文档。</span></p>
<p><span style="font-size:14px;color:#9999ff;">Android 6.0行为变更</span></p>
<p><span style="font-size:14px;">API级别：23</span></p>
<p><span style="font-size:14px;color:#f00;">1. 运行时权限</span></p>
<p><span style="font-size:14px;">对于以 Android 6.0(API 级别 23)或更高版本为目标平台的应用，请务必在运行时检查和请求权限。要确定您的应用是否已被授予权限，请调用新增的 checkSelfPermission() 方法。要请求权限，请调用新增的 requestPermissions() 方法。即使您的应用并不以 Android 6.0(API 级别 23)为目标平台，您也应该在新权限模式下测试您的应用。</span></p>
<p><span style="font-size:14px;color:#f00;">2. 取消支持Apache HTTP客户端</span></p>
<p><span style="font-size:14px;">Android 6.0 版移除了对 Apache HTTP 客户端的支持。如果您的应用使用该客户端，并以 Android 2.3(API 级别 9)或更高版本为目标平台，请改用 HttpURLConnection 类。此 API 效率更高，因为它可以通过透明压缩和响应缓存减少网络使用，并可最大限度降低耗电量。要继续使用 Apache HTTP API，您必须先在 build.gradle
 文件中声明以下编译时依赖项：</span></p>
<p><span style="font-size:14px;">android {</span></p>
<p><span style="font-size:14px;">useLibrary 'org.apache.http.legacy'</span></p>
<p><span style="font-size:14px;">}</span></p>
<p><span style="font-size:14px;color:#f00;">3. BoringSSL</span></p>
<p><span style="font-size:14px;">Android 正在从使用 OpenSSL 库转向使用 BoringSSL 库。如果您要在应用中使用 Android NDK，请勿链接到并非 NDK API 组成部分的加密库，如 libcrypto.so 和 libssl.so。这些库并非公共 API，可能会在不同版本和设备上毫无征兆地发生变化或出现故障。此外，您还可能让自己暴露在安全<a href="https://www.2cto.com/" rel="nofollow" class="keylink">漏洞</a>的风险之下。请改为修改原生代码，以通过
 JNI 调用 Java 加密 API，或静态链接到您选择的加密库。</span></p>
<p><span style="font-size:14px;color:#f00;">4. 通知</span></p>
<p><span style="font-size:14px;">此版本移除了Notification.setLatestEventInfo()方法。请改用 Notification.Builder 类来构建通知。要重复更新通知，请重复使用 Notification.Builder 实例。调用 build() 方法可获取更新后的 Notification 实例。</span></p>
<p><span style="font-size:14px;">adb shell dumpsys notification命令不再打印输出您的通知文本。请改用adb shell dumpsys notification --noredact命令打印输出 notification 对象中的文本。</span></p>
<p><span style="font-size:14px;color:#f00;">5. 音频管理器变更</span></p>
<p><span style="font-size:14px;">不再支持通过 AudioManager 类直接设置音量或将特定音频流静音。setStreamSolo() 方法已弃用，您应该改为调用 requestAudioFocus() 方法。类似地，setStreamMute() 方法也已弃用，请改为调用 adjustStreamVolume() 方法并传入方向值 ADJUST_MUTE 或 ADJUST_UNMUTE。</span></p>
<p><span style="font-size:14px;color:#f00;">6. 相机服务变更</span></p>
<p><span style="font-size:14px;">在此版本中，相机服务中共享资源的访问模式已从之前的“先到先得”访问模式更改为高优先级进程优先的访问模式。对服务行为的变更包括：</span></p>
<p><span style="font-size:14px;">根据客户端应用进程的“优先级”授予对相机子系统资源的访问权，包括打开和配置相机设备。带有对用户可见 Activity 或前台Activity 的应用进程一般会被授予较高的优先级，从而使相机资源的获取和使用更加可靠;</span></p>
<p><span style="font-size:14px;">当高优先级的应用尝试使用相机时，系统可能会“驱逐”正在使用相机客户端的低优先级应用。在已弃用的 Camera API 中，这会导致系统为被驱逐的客户端调用 onError()。在 Camera2 API 中，这会导致系统为被驱逐的客户端调用onDisconnected();</span></p>
<p><span style="font-size:14px;">在配备相应相机硬件的设备上，不同的应用进程可同时独立打开和使用不同的相机设备。但现在，如果在多进程用例中同时访问相机会造成任何打开的相机设备的性能或能力严重下降，相机服务会检测到这种情况并禁止同时访问。即使并没有其他应用直接尝试访问同一相机设备，此变更也可能导致低优先级客户端被“驱逐”。</span></p>
<p><span style="font-size:14px;">更改当前用户会导致之前用户帐户拥有的应用内活动相机客户端被驱逐。对相机的访问仅限于访问当前设备用户拥有的用户个人资料。举例来说，这意味着，当用户切换到其他帐户后，“来宾”帐户实际上无法让使用相机子系统的进程保持运行状态</span></p>
<p><span style="color:#9999ff;"><span style="font-weight:bold;"><span style="font-size:14px;">Android 7.0行为变更</span></span></span></p>
<p><span style="font-size:14px;">API级别：24</span></p>
<p><span style="font-size:14px;color:#f00;">1. 电池和内存</span></p>
<p><span style="font-size:14px;">Android 7.0 包括旨在延长设备电池寿命和减少 RAM 使用的系统行为变更。这些变更可能会影响您的应用访问系统资源，以及您的应用通过特定隐式 intent 与其他应用交互的方式。</span></p>
<p><span style="font-size:14px;color:#f00;">2. Project Svelte：后台优化</span></p>
<p><span style="font-size:14px;">Android 7.0 移除了三项隐式广播，以帮助优化内存使用和电量消耗。此项变更很有必要，因为隐式广播会在后台频繁启动已注册侦听这些广播的应用。删除这些广播可以显著提升设备性能和用户体验。</span></p>
<p><span style="font-size:14px;">移动设备会经历频繁的连接变更，例如在 WLAN 和移动数据之间切换时。目前，可以通过在应用清单中注册一个接收器来侦听隐式 CONNECTIVITY_ACTION 广播，让应用能够监控这些变更。由于很多应用会注册接收此广播，因此单次网络切换即会导致所有应用被唤醒并同时处理此广播。</span></p>
<p><span style="font-size:14px;">同理，在之前版本的 Android 中，应用可以注册接收来自其他应用(例如相机)的隐式 ACTION_NEW_PICTURE 和 ACTION_NEW_VIDEO 广播。当用户使用相机应用拍摄照片时，这些应用即会被唤醒以处理广播。</span></p>
<p><span style="font-size:14px;">为缓解这些问题，Android 7.0 应用了以下优化措施：</span></p>
<p><span style="font-size:14px;">面向 Android 7.0 开发的应用不会收到 CONNECTIVITY_ACTION 广播，即使它们已有清单条目来请求接受这些事件的通知。在前台运行的应用如果使用 BroadcastReceiver 请求接收通知，则仍可以在主线程中侦听 CONNECTIVITY_CHANGE。</span></p>
<p><span style="font-size:14px;">应用无法发送或接收 ACTION_NEW_PICTURE 或 ACTION_NEW_VIDEO 广播。此项优化会影响所有应用，而不仅仅是面向 Android 7.0 的应用。</span></p>
<p><span style="font-size:14px;">如果您的应用使用任何 intent，您仍需要尽快移除它们的依赖关系，以正确适配 Android 7.0 设备。Android 框架提供多个解决方案来缓解对这些隐式广播的需求。例如，JobScheduler API 提供了一个稳健可靠的机制来安排满足指定条件(例如连入无限流量网络)时所执行的网络操作。您甚至可以使用 JobScheduler 来适应内容提供程序变化。</span></p>
<p><span style="font-size:14px;color:#f00;">3. 系统权限更改</span></p>
<p><span style="font-size:14px;">为了提高私有文件的安全性，面向 Android 7.0 或更高版本的应用私有目录被限制访问　(0700)。此设置可防止私有文件的元数据泄漏，如它们的大小或存在性。此权限更改有多重副作用：</span></p>
<p><span style="font-size:14px;">1.私有文件的文件权限不应再由所有者放宽，为使用 MODE_WORLD_READABLE 和/或 MODE_WORLD_WRITEABLE 而进行的此类尝试将触发 SecurityException。</span></p>
<p><span style="font-size:14px;">注：迄今为止，这种限制尚不能完全执行。应用仍可能使用原生 API 或 File API 来修改它们的私有目录权限。但是，我们强烈反对放宽私有目录的权限。</span></p>
<p><span style="font-size:14px;">2.传递软件包网域外的 file:// URI 可能给接收器留下无法访问的路径。因此，尝试传递 file:// URI 会触发 FileUriExposedException。分享私有文件内容的推荐方法是使用 FileProvider。</span></p>
<p><span style="font-size:14px;">3.DownloadManager 不再按文件名分享私人存储的文件。旧版应用在访问 COLUMN_LOCAL_FILENAME 时可能出现无法访问的路径。面向 Android 7.0 或更高版本的应用在尝试访问 COLUMN_LOCAL_FILENAME 时会触发 SecurityException。通过使用DownloadManager.Request.setDestinationInExternalFilesDir()或DownloadManager.Request.setDestinationInExternalPublicDir()将下载位置设置为公共位置的旧版应用仍可以访问
 COLUMN_LOCAL_FILENAME 中的路径，但是我们强烈反对使用这种方法。对于由 DownloadManager 公开的文件，首选的访问方式是使用ContentResolver.openFileDescriptor()。</span></p>
<p><span style="font-size:14px;color:#f00;">4. 在应用件共享文件</span></p>
<p><span style="font-size:14px;">对于面向 Android 7.0 的应用，Android 框架执行的 StrictMode API 政策禁止在您的应用外部公开 file:// URI。如果一项包含文件 URI 的 intent 离开您的应用，则应用出现故障，并出现 FileUriExposedException 异常。</span></p>
<p><span style="font-size:14px;">要在应用间共享文件，您应发送一项 content:// URI，并授予 URI 临时访问权限。进行此授权的最简单方式是使用 FileProvider 类。</span></p>
<p><span style="font-size:14px;color:#f00;">5. 屏幕缩放</span></p>
<p><span style="font-size:14px;">Android 7.0 支持用户设置显示尺寸，以放大或缩小屏幕上的所有元素，从而提升设备对视力不佳用户的可访问性。用户无法将屏幕缩放至低于最小屏幕宽度 sw320dp，该宽度是 Nexus 4 的宽度，也是常规中等大小手机的宽度。</span></p>
<p><span style="font-size:14px;">当设备密度发生更改时，系统会以如下方式通知正在运行的应用：</span></p>
<p><span style="font-size:14px;">如果是面向 API 级别 23 或更低版本系统的应用，系统会自动终止其所有后台进程。这意味着如果用户切换离开此类应用，转而打开 Settings 屏幕并更改 Display size 设置，则系统会像处理内存不足的情况一样终止该应用。如果应用具有任何前台进程，则系统会如处理运行时更改中所述将配置变更通知给这些进程，就像对待设备屏幕方向变更一样。</span></p>
<p><span style="font-size:14px;">如果是面向 Android 7.0 的应用，则其所有进程(前台和后台)都会收到有关配置变更的通知，如处理运行时更改中所述。</span></p>
<p><span style="font-size:14px;">大多数应用并不需要进行任何更改即可支持此功能，不过前提是这些应用遵循 Android 最佳做法。具体要检查的事项：</span></p>
<p><span style="font-size:14px;">1.在屏幕宽度为 sw320dp 的设备上测试您的应用，并确保其充分运行。</span></p>
<p><span style="font-size:14px;">2.当设备配置发生变更时，更新任何与密度相关的缓存信息，例如缓存位图或从网络加载的资源。当应用从暂停状态恢复运行时，检查配置变更。</span></p>
<p><span style="font-size:14px;">注：如果您要缓存与配置相关的数据，则最好也包括相关元数据，例如该数据对应的屏幕尺寸或像素密度。保存这些元数据便于您在配置变更后决定是否需要刷新缓存数据。</span></p>
<p><span style="font-size:14px;">3.避免用像素单位指定尺寸，因为像素不会随屏幕密度缩放。应改为使用与密度无关像素 (dp) 单位指定尺寸。</span></p>
<p><span style="font-size:14px;color:#f00;">6. 检查你的应用是否使用私有库</span></p>

<p><span style="font-size:14px;">为帮助您识别加载私有库的问题，logcat 可能会生成一个警告或运行时错误。例如，如果您的应用面向 API 级别 23 或更低级别，并在运行 Android 7.0 的设备上尝试访问私有库，您可能会看到一个类似于下面所示的警告：</span></p>
<p><span style="font-size:14px;">03-21 17:07:51.502 31234 31234 W linker :</span></p>
<p><span style="font-size:14px;">library "libandroid_runtime.so"("/system/lib/libandroid_runtime.so") needed or dlopened by "/data/app/com.popular-app.android-2/lib/arm/libapplib.so" is not accessible for the namespace
 "classloader-namespace" - the access is temporarily granted as a workaround for https://b/26394120</span></p>
<p><span style="font-size:14px;">这些 logcat 警告通知您哪个库正在尝试访问私有平台 API，但不会导致您的应用崩溃。但是，如果应用面向 API 级别 24 或更高级别，logcat 会生成以下运行时错误，您的应用可能会崩溃：</span></p>
<p><span style="font-size:14px;">java.lang.UnsatisfiedLinkError: dlopen failed:</span></p>
<p><span style="font-size:14px;">library "libcutils.so"("/system/lib/libcutils.so") needed or dlopened by"/system/lib/libnativeloader.so" is not accessible for the namespace "classloader-namespace"</span></p>
<p><span style="font-size:14px;">at java.lang.Runtime.loadLibrary0(Runtime.java:977)</span></p>
<p><span style="font-size:14px;">at java.lang.System.loadLibrary(System.java:1602)</span></p>
<p><span style="font-size:14px;">如果您的应用使用动态链接到私有平台 API 的第三方库，您可能也会看到上述 logcat 输出。利用 Android 7.0DK 中的 readelf 工具，您可以通过运行以下命令生成给定 .so 文件的所有动态链接的共享库列表：</span></p>
<p><span style="font-size:14px;">aarch64-linux-android-readelf -dW libMyLibrary.so</span></p>
<p><span style="font-size:14px;color:#f00;">7. 其他重要说明</span></p>
<p><span style="font-size:14px;">⑴如果一个应用在 Android 7.0 上运行，但却是针对更低 API 级别开发的，那么在用户更改显示尺寸时，系统将终止此应用进程。应用必须能够妥善处理此情景。否则，当用户从最近使用记录中恢复运行应用时，应用将会出现崩溃现象。</span></p>
<p><span style="font-size:14px;">您应测试应用以确保不会发生此行为。要进行此测试，您可以通过 DDMS 手动终止应用，以造成相同的崩溃现象。</span></p>
<p><span style="font-size:14px;">在密度发生更改时，系统不会自动终止面向 N 及更高版本的应用;不过，这些应用仍可能对配置变更做出不良响应。</span></p>
<p><span style="font-size:14px;">⑵Android 7.0 上的应用应能够妥善处理配置变更，并且在后续启动时不会出现崩溃现象。您可以通过更改字体大小 (Setting &gt;Display &gt; Font size) 并随后从最近使用记录中恢复运行应用，来验证应用行为。</span></p>
<p><span style="font-size:14px;">⑶由于之前的 Android 版本中的一项错误，系统未能将对主线程上的一个 TCP 套接字的写入操作举报为违反严格模式。Android 7.0 修复了此错误。呈现出这种行为的应用现在会引发android.os.NetworkOnMainThreadException。一般情况下，我们不建议在主线程上执行网络操作，因为这些操作通常会出现可能导致 ANR 和卡顿的高尾延迟。</span></p>
<p><span style="font-size:14px;">⑷Debug.startMethodTracing()方法系列现在默认在您的共享存储空间上的软件包特定目录中存储输出，而非 SD 卡根目录。这意味着应用不再需要请求WRITE_EXTERNAL_STORAGE权限来使用这些 API 。</span></p>
<p><span style="font-size:14px;">⑸许多平台 API 现在开始检查在 Binder 事务间发送的大负载，系统现在会将TransactionTooLargeExceptions作为 RuntimeExceptions 再次引发，而不再只是默默记录或抑制它们。一个常见例子是在Activity.onSaveInstanceState()上存储过多数据，导致ActivityThread.StopInfo在您的应用面向
 Android 7.0 时引发 RuntimeException。</span></p>
<p><span style="font-size:14px;">⑹如果应用向 View 发布 Runnable 任务，并且 View 未附加到窗口，系统会用 View 为 Runnable 任务排队;在 View 附加到窗口之前，不会执行 Runnable 任务。此行为会修复以下错误：</span></p>
<p><span style="font-size:14px;">如果一项应用是从并非预期窗口 UI 线程的其他线程发布到 View，则 Runnable 可能会因此运行错误的线程。</span></p>
<p><span style="font-size:14px;">如果 Runnable 任务是从并非环路线程的其他线程发布，则应用可能会曝光 Runnable 任务。</span></p>
<p><span style="font-size:14px;">⑺如果 Android 7.0 上一项有 DELETE_PACKAGES 权限的应用尝试删除一个软件包，但另一项应用已经安装了这个软件包，则系统需要用户进行确认。在这种情况下，应用在调用PackageInstaller.uninstall()时预计的返回状态应为STATUS_PENDING_USER_ACTION。</span></p>
<p><span style="font-size:14px;">⑻名为 Crypto 的 JCA 提供程序已弃用，因为它仅有的 SHA1PRNG 算法为弱加密。应用无法再使用 SHA1PRNG(不安全地)派生密钥，因为不再提供此提供程序。</span></p>

<p><span style="font-weight:bold;"><span style="font-size:14px;color:#9999ff;">Android 8.0新特性</span></span></p>


<p><span style="font-size:14px;color:#f00;">1、Android 8.0 大幅提升了开机速度</span></p>
<p><span style="font-size:14px;">对 Pixel 而言，开机速度提升了一倍，和旗舰机型三星 Galaxy S8 对比，嗯，看看开心就好。</span></p>
<p><span style="font-size:14px;">Android 8.0二十大新特性，这些地方像极了iOS?</span></p>
<p><span style="font-size:14px;color:#f00;">2、锁屏界面变化很小，字号缩小了一圈，为锁屏壁纸和通知等内容留出更多视觉空间</span></p>
<p><span style="font-size:14px;">不过，在动辄 0.1、0.2 秒解锁的指纹识别普及后，锁屏界面已不那么重要了。</span></p>
<p><span style="font-size:14px;">Android 8.0二十大新特性，这些地方像极了iOS?</span></p>
<p><span style="font-size:14px;color:#f00;">3、桌面更新体现在「可自定义图标的形状」上</span></p>
<p><span style="font-size:14px;">在 Pixel 桌面，你可以为图标选择圆形、方形或者圆角矩形等样式。另一个细节是，以前在 Google Play 市场设置的「将新应用图标添加到桌面」选项，如今需要在 Pixel 桌面中设置。</span></p>
<p><span style="font-size:14px;">Android 8.0二十大新特性，这些地方像极了iOS?</span></p>
<p><span style="font-size:14px;">五种桌面图标形状</span></p>
<p><span style="font-size:14px;color:#f00;">4、引入了「通知圆点」功能，但不会显示具体通知数量，只会在图标右上角显示一个圆点</span></p>
<p><span style="font-size:14px;">这儿有个细节，这个出现在右上角的圆点，会从图标左下角提取颜色，所以每个 APP 的圆点都是不一样的颜色。</span></p>
<p><span style="font-size:14px;">Android 8.0二十大新特性，这些地方像极了iOS?</span></p>
<p><span style="font-size:14px;color:#f00;">5、长按图标，能看到图标菜单和通知概览</span></p>
<p><span style="font-size:14px;">长按即可。目前最实用的，是支付宝的快捷付款功能。</span></p>
<p><span style="font-size:14px;color:#f00;">6、全新的状态栏</span></p>
<p><span style="font-size:14px;">底色从之前的黑色，到第一个开发者预览版时的黑白任选，再到正式版的只剩下白色，看起来清爽不少，动画也更优雅。</span></p>
<p><span style="font-size:14px;">Android 8.0二十大新特性，这些地方像极了iOS?</span></p>
<p><span style="font-size:14px;color:#f00;">7、通知栏变得更加可爱</span></p>
<p><span style="font-size:14px;">系统只默认完整显示最顶部的通知，其余通知被压缩，可以用手势下拉查看全部内容。还有就是， Google Play Music 和 YouTuBe 的通知，会根据内容或专辑封面增添通知色彩。</span></p>
<p><span style="font-size:14px;">Android 8.0二十大新特性，这些地方像极了iOS?</span></p>
<p><span style="font-size:14px;color:#f00;">8、在展开或缩起所有通知时，最左边的小图标会有可爱的动画出现</span></p>
<p><span style="font-size:14px;">Android 8.0二十大新特性，这些地方像极了iOS?</span></p>
<p><span style="font-size:14px;">↑留意通知栏左下角↑</span></p>
<p><span style="font-size:14px;color:#f00;">9、设置界面相对与 Android 7.1.2 引入了层级概念</span></p>
<p><span style="font-size:14px;">将不常用设置项归纳到一起，保持整体的简洁，但也增加了寻找的难度。</span></p>
<p><span style="font-size:14px;">Android 8.0二十大新特性，这些地方像极了iOS?</span></p>
<p><span style="font-size:14px;">设置界面</span></p>
<p><span style="font-size:14px;color:#f00;">10、系统应用的默认图标统一更新为绿色圆形</span></p>
<p><span style="font-size:14px;">这个图标除了系统应用外，一些懒得画图标的第三方应用也可以直接用上，呵呵，这些开发者是有多懒。</span></p>
<p><span style="font-size:14px;">Android 8.0二十大新特性，这些地方像极了iOS?</span></p>
<p><span style="font-size:14px;color:#f00;">11、安全性选项中，Android 8.0 引入了「Google Play 保护机制」</span></p>
<p><span style="font-size:14px;">它会定期检查手机所安装的应用是否存在有害行为，如果发现安全风险，系统会通知用户。</span></p>
<p><span style="font-size:14px;color:#f00;">12、每个 APP 的「安装未知应用」功能将默认被限制</span></p>
<p><span style="font-size:14px;">比如在 Chrome 浏览器上下载一个 apk 安装包，如果未经允许，这个安装包是无法安装的。安装应用的过程中有明确进度条可以查看。</span></p>
<p><span style="font-size:14px;color:#f00;">13、终于可以直接在铃声设置界面添加第三方手机铃声</span></p>
<p><span style="font-size:14px;">不用将喜欢的铃声放进 ringtones 文件夹了。</span></p>
<p><span style="font-size:14px;">接下来要说的两个功能，几乎是到了最后的第四个开发者预览版才能够正常使用。</span></p>
<p><span style="font-size:14px;color:#f00;">14、画中画模式</span></p>
<p><span style="font-size:14px;">使用 Chrome 全屏播放视频或者在 YouTuBe 观看视频时，按下 Home 键就可以进入画中画模式。</span></p>
<p><span style="font-size:14px;color:#f00;">15、Autofill 功能</span></p>
<p><span style="font-size:14px;">能够通过你存储在谷歌帐号上的帐号密码，自动在登录应用时填充。</span></p>
<p><span style="font-size:14px;color:#f00;">16、在 Android 8.0 的开发者选项中，还出现了蓝牙音频解码器加</span></p>
<p><span style="font-size:14px;">入了由索尼提供的 LDAC 无线音效技术，索尼蓝牙耳机用户有福了。另外，像 aptX 和 aptX HD等无线技术也有提供。</span></p>
<p><span style="font-size:14px;">在没有开启开发者选项的情况下，系统会自动帮你做出选择，比如在连接索尼蓝牙耳机后，会自动切换到 LDAC 模式，而连接三星蓝牙耳机时，会切换回 aptX。</span></p>
<p><span style="font-size:14px;color:#f00;">17、智能文本选择</span></p>
<p><span style="font-size:14px;">举个例子，在邮件中选择一个带地址的文本，系统除了弹出复制和全选之外，还会直接提供谷歌地图的快捷方式，让用户直接在地图中查看这个地址。</span></p>
<p><span style="font-size:14px;color:#f00;">18、Pixel 自带相机中增加了双击放大功能</span></p>
<p><span style="font-size:14px;">这功能可能是为双摄两倍变焦做准备的。</span></p>
<p><span style="font-size:14px;color:#f00;">19、Emoji 表情也从之前的果冻变成了圆形</span></p>
<p><span style="font-size:14px;">个人感觉是没之前的可爱。</span></p>


<p><span style="font-size:14px;color:#9999ff;"><span style="font-weight:bold;">Android 9.0行为变更</span></span></p>



<h3 id="室内wifi定位">室内WIFI定位</h2>

<p >Android P增加了对RTT Wi-Fi协议的支持，以此作为室内定位的基础。 <br>
在支持硬件支持的Android P设备上，开启定位并且打开WIFI扫描后就可以使用该功能进行定位。应用可以测量与附近支持RTT的Wi-Fi接入点（AP）的距离。设备必须启用位置并启用Wi-Fi扫描（在设置&gt;位置下）。使用这个功能不会连接到WIFI，而且为了保持隐私，只有手机能确定AP到设备的距离，反之则不能。 <br>
如果设备测量到3个或更多AP的距离，则可以使用多点定位算法来估算最适合这些测量值的设备位置。其结果通常可以精确到1至2米范围。</p>





<p>该功能API在android.net.wifi.rtt下。</p>



<h2 id="刘海屏幕支持">“刘海”屏幕支持</h2>

<p>Android P 支持了手机屏幕是不规则形状时的获取（主要是应对刘海屏吧）。可以使用类似windowInsets.getDisplayCutout()来获取一些你想要的信息。</p>



<pre class="prettyprint"><code class="language-java hljs "><span class="hljs-comment">//您可以在自己的View中获取到不应该绘制的部分屏幕</span>
getRootWindowInsets().getDisplayCutout().getBounds();
getRootWindowInsets().getDisplayCutout().getSafeInsetBottom();
getRootWindowInsets().getDisplayCutout().getSafeInsetLeft();
getRootWindowInsets().getDisplayCutout().getSafeInsetRight();
getRootWindowInsets().getDisplayCutout().getSafeInsetTop();
<span class="hljs-comment">//也可以设置Window的属性</span>
WindowManager windowManager = (WindowManager) getApplicationContext().getSystemService(Context.WINDOW_SERVICE);
WindowManager.LayoutParams layoutParams = <span class="hljs-keyword">new</span> WindowManager.LayoutParams();
layoutParams.layoutInDisplayCutoutMode = WindowManager.LayoutParams.LAYOUT_IN_DISPLAY_CUTOUT_MODE_ALWAYS;
layoutParams.layoutInDisplayCutoutMode = WindowManager.LayoutParams.LAYOUT_IN_DISPLAY_CUTOUT_MODE_DEFAULT;
layoutParams.layoutInDisplayCutoutMode = WindowManager.LayoutParams.LAYOUT_IN_DISPLAY_CUTOUT_MODE_NEVER;</code></pre>



<h2 id="通知">通知</h2>

<p>Android P还增加了许多对通知的支持。</p>



<h3 id="增强体验">增强体验</h3>

<p>从Android 7.0开始，就优化了Android通知栏的体验。 <br>
在P当中，又新增了下述功能： <br>
支持图像：Android P现在在手机上的消息通知中显示图像。您可以在消息上使用setData（）来显示图像。 <br>
会话参与者的简化支持：新的Notification.Person类用于标记参与聊天的人，包括他们的头像和URI。还有其他的一些API，现在都用Person类作为标志参数而不是CharSequence。</p>



<pre class="prettyprint"><code class="language-java hljs ">Notification.Builder builder = <span class="hljs-keyword">new</span> Notification.Builder(<span class="hljs-keyword">this</span>, <span class="hljs-string">"a"</span>);
<span class="hljs-comment">//新的聊天对象</span>
Notification.Person p = <span class="hljs-keyword">new</span> Notification.Person();
<span class="hljs-comment">//在MessagingStyle中用Person代替了以往的CharSequence</span>
Notification.MessagingStyle messageStyle = <span class="hljs-keyword">new</span> Notification.MessagingStyle(p);
Notification.MessagingStyle.Message message = <span class="hljs-keyword">new</span> Notification.MessagingStyle.Message(<span class="hljs-string">"aaa"</span>, <span class="hljs-number">100</span>, p);
<span class="hljs-comment">//可以显示图像了</span>
message.setData();
messageStyle.addMessage(message);
builder.setStyle(messageStyle);
Notification notification = builder.build();</code></pre>

<p><strong>将回复另存为草稿</strong>：当用户无意中关闭消息通知时，您的应用可以检索系统发送的EXTRA_REMOTE_INPUT_DRAFT来获取一些信息。 <br>
<strong>确定对话是否是群组对话</strong>：您可以使用setGroupConversation（）来有目的地将对话标识为群组对话或非群组对话。 <br>
<strong>为意图设置语义动作</strong>：setSemanticAction（）方法允许您为某个动作提供语义含义，如标记为读取，删除，回复等。 <br>
<strong>SmartReply</strong></p>



<h3 id="通道设置广播以及免打扰">通道设置、广播以及免打扰</h3>

<p>Android O引入了Notification Channels，可让您为要显示的每种类型的通知创建一个用户可自定义的频道。 Android P通过以下更改简化了通知渠道设置： <br>
<strong>阻止渠道</strong>：用户现在可以在应用的通知设置中阻止整组渠道。您可以使用isBlocked（）方法来确定某个组何时被阻止，不对被阻止的组发送消息。 <br>
此外，您的应用可以使用新的getNotificationChannelGroup（）方法查询当前渠道设置。 <br>
<strong>新的广播类型</strong>：Android系统现在在通知频道和频道组的阻塞状态发生变化时发送广播。拥有被阻止的频道或群组的应用可以监听这些Intent并作出相应的反应。有关这些Intent的更多信息，请参阅<a href="https://developer.android.com/reference/android/app/NotificationManager.html#constants" rel="nofollow">NotificationManager</a>参考中更新后的常量列表。有关对广播Intent作出反应的信息，请参阅<a href="https://developer.android.com/guide/components/broadcasts.html" rel="nofollow">广播</a>。 <br>
<strong>新的免打扰优先级类别</strong>：NotificationManager.Policy有两个新的策略常量：PRIORITY_CATEGORY_ALARMS（按优先级排列）和PRIORITY_CATEGORY_MEDIA_SYSTEM_OTHER（优先排列媒体，系统和游戏声音）</p>

<h2 id="多相机支持和相机更新">多相机支持和相机更新</h2>

<p>现在，可以同时从两个或更多的物理摄像头同时获得数据流。在具有双前置或双后置摄像头的设备上，可以实现无法使用单个摄像头实现的功能，例如无缝缩放，散景 ，和立体视觉。 该API还允许您调用合理的或者融合的相机流，以便在两台或更多台相机之间自动切换。 <br>
相机的其他改进包括新的<code>android.hardware.camera2.params.SessionConfiguration</code>，有助于减少初始捕捉期间的延迟。而Surface共享可让相机客户端处理各种使用情况，而无需停止和启动相机流式传输。 此外还添加了基于显示的闪光灯支持的<a href="https://developer.android.com/reference/android/hardware/camera2/CameraMetadata.html#CONTROL_AE_MODE_ON_EXTERNAL_FLASH" rel="nofollow">API</a>。 <br>
Android P还支持支持deveices上的<a href="android.hardware.camera2.CameraCharacteristics" rel="nofollow">外部USB / UVC相机</a>。</p>



<h2 id="新的图片解码">新的图片解码</h2>

<p>Android P新增了<a href="https://developer.android.com/reference/android/graphics/ImageDecoder.html" rel="nofollow">ImageDecoder</a>类，为解码图像提供了一种更优的方法。由此可以用ImageDecoder来替换BitmapFactory和BitmapFactory.Options。更多使用方法请参见官方API。</p>



<pre class="prettyprint"><code class="language-java hljs ">String filePath = <span class="hljs-string">"test"</span>;
File file = <span class="hljs-keyword">new</span> File(filePath);
ImageDecoder.Source source = ImageDecoder.createSource(file);
ImageDecoder.decodeBitmap(source);
ImageDecoder.decodeDrawable(source, (imageDecoder, imageInfo, source1) -&gt; {
    <span class="hljs-comment">//裁剪图像</span>
    imageDecoder.setCrop();
    <span class="hljs-comment">//调整大小</span>
    imageDecoder.setResize();
});
BitmapFactory.decodeFile(filePath);</code></pre>



<h2 id="动画">动画</h2>

<p>Android P引入了一个新的AnimatedImageDrawable类来绘制和显示GIF和WebP动画图像。 AnimatedImageDrawable与AnimatedVectorDrawable类似，因为AnimatedImageDrawable动画也是基于RenderThread工作的。 RenderThread本身在内部使用工作线程进行解码，因此解码不会干扰RenderThread。 这种实现允许您的应用拥有动画图像，而无需管理其更新或干扰应用的UI线程。</p>



<pre class="prettyprint"><code class="language-java hljs ">Drawable d = ImageDecoder.decodeDrawable(...);
<span class="hljs-keyword">if</span> (d <span class="hljs-keyword">instanceof</span> AnimatedImageDrawable) {
    <span class="hljs-comment">// Prior to start(), the first frame is displayed</span>
    ((AnimatedImageDrawable) d).start();  
}</code></pre>



<h2 id="hdr-vp9视频heif图像压缩和媒体api">HDR VP9视频，HEIF图像压缩和媒体API</h2>

<p>Android P增加了对HDR VP9 Profile 2的内置支持。</p>

<p>Android P支持HEIF图像（隔壁IOS在2017年10月推的新的图片编码）编码。  <br>
Android P还引入了MediaPlayer2。该播放器支持使用DataSourceDesc构建的播放列表。</p>



<pre class="prettyprint"><code class="language-java hljs ">MediaPlayer2.create();</code></pre>

<p>注：笔者对图像/视频编解码方面不甚了了，有兴趣的可以自行参阅<a href="https://developer.android.com/sdk/api_diff/p-dp1/changes.html" rel="nofollow">API</a>。</p>



<h2 id="jobscheduler中的数据成本敏感度">JobScheduler中的数据成本敏感度</h2>

<p>在Android P当中，JobScheduler得到了改进，使其能够更好地为用户处理与网络相关的工作，并配合运营商分别提供网络状态信号。 <br>
Jobs现在可以定义出其估计的数据大小，预取信号，并指定详细的网络要求 - 运营商可以将网络报告为拥塞或不用流量计费的。然后，JobScheduler根据网络状态管理工作。例如，当网络拥塞时，JobScheduler可能推迟大型网络请求。在不用流量计费的的网络上时，JobScheduler可以预读来改进用户体验。</p>



<h2 id="神经网络api-11">神经网络API 1.1</h2>

<p>对神经网络API新增了9个功能：Pad, BatchToSpaceND, SpaceToBatchND, Transpose, Strided Slice, Mean, Div, Sub, and Squeeze。</p>



<h2 id="改进表单自动填充">改进表单自动填充</h2>

<p>Android 8.0（API26）引入了自动填充框架，这使得在应用中填写表单变得更加容易。 Android P引入了自动填充服务并实现了多项改进，以在填写表单时进一步增强用户体验。 有关更多详细信息，请参阅<a href="https://developer.android.com/preview/features/autofill.html" rel="nofollow">自动填充框架</a>。 <br>
注：该自动填充框架笔者应是Google服务中的内容，国内用户可能会体验不到（或许有厂商自己的版本）。</p>



<h2 id="安全增强">安全增强</h2>

<p>Android P引入了许多新的安全功能，包括统一的指纹验证对话框和敏感交易的高确信度的用户确认。 有关更多详细信息，请参阅<a href="https://developer.android.com/preview/features/security.html" rel="nofollow">安全更新</a>页面。</p>



<h2 id="android-备份加密">Android 备份加密</h2>

<p>Android P支持使用客户端密钥对Android备份进行加密。 这项隐私措施，需要设备的PIN，图案密码或标准密码才能从用户设备备份的数据中恢复数据。 <br>
要了解有关在Android设备上备份数据的更多信息，请参阅数据<a href="https://developer.android.com/guide/topics/data/backup.html" rel="nofollow">备份概述</a>。 <br>
注：据笔者所知，国内厂商基本都做了自己的备份系统（或者和其他大厂合作），所以没兴趣的同学散了吧。</p>
