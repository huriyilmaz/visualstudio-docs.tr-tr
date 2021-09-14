---
title: Tam zamanında hata ayıklayıcı kullanarak hata ayıklayın | Microsoft Docs
description: Visual Studio içinde tam zamanında hata ayıklayıcı kullanarak hata ayıklayın. tam zamanında hata ayıklama, bir uygulama hataları veya kilitlenmeleri sırasında otomatik olarak Visual Studio başlatabilir.
ms.custom: SEO-VS-2020
ms.date: 08/24/2021
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8be534863936f44ce5a43e08d317c8cdb6e96c38
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626522"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Visual Studio içinde tam zamanında hata ayıklayıcı kullanarak hata ayıklayın

tam zamanında hata ayıklama, Visual Studio hataları veya kilitlenmeler dışında çalışan bir uygulama olduğunda otomatik olarak Visual Studio başlatabilir. tam zamanında hata ayıklama sayesinde uygulamaları Visual Studio dışında test edebilir ve bir sorun oluştuğunda hata ayıklamaya başlamak için Visual Studio açabilirsiniz.

tam zamanında hata ayıklama Windows masaüstü uygulamalarında çalışmaktadır. evrensel Windows uygulamalarında veya görselleştiriciler gibi yerel bir uygulamada barındırılan yönetilen kod için çalışmaz.

> [!TIP]
> yalnızca tam zamanında hata ayıklayıcı iletişim kutusunun görüntülenmesini durdurmak istiyorsanız, ancak Visual Studio yüklü değilse, [tam zamanında hata ayıklayıcıyı devre dışı bırakma](../debugger/just-in-time-debugging-in-visual-studio.md)konusuna bakın. Visual Studio bir kez yüklüyse, [Windows kayıt defterinden tam zamanında hata ayıklamayı devre dışı bırakmanız](#disable-just-in-time-debugging-from-the-windows-registry)gerekebilir.

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a>Visual Studio içinde tam zamanında hata ayıklamayı etkinleştirme veya devre dışı bırakma

>[!NOTE]
>tam zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak için Visual Studio yönetici olarak çalıştırıyor olmanız gerekir. Tam zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak bir kayıt defteri anahtarı ayarlar ve bu anahtarı değiştirmek için yönetici ayrıcalıkları gerekebilir. Visual Studio yönetici olarak açmak için, Visual Studio uygulamasına sağ tıklayın ve **yönetici olarak çalıştır**' ı seçin.

Visual Studio **araçları**  >  **seçenekleri** (veya **hata ayıklama**  >  **seçenekleri**) iletişim kutusundan tam zamanında hata ayıklamayı yapılandırabilirsiniz.

**Tam zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak için:**

1. **Araçlar** veya **Hata Ayıkla** menüsünde,   >    >  **tam zamanında** hata ayıklama seçenekleri ' ni seçin.

   ![JıT hata ayıklamayı etkinleştirme veya devre dışı bırakma](../debugger/media/dbg-jit-enable-or-disable.png "JIT hata ayıklamayı etkinleştirme veya devre dışı bırakma")

1. **Bu kod türleri Için tam zamanında hata ayıklamayı etkinleştir** kutusunda hata ayıklamada tam zamanında hata ayıklamayı istediğiniz kod türlerini seçin: **yönetilen**, **Yerel** ve/veya **betiği**.

1. **Tamam**’ı seçin.

Just-In-Time hata ayıklayıcıyı etkinleştirirseniz, ancak bir uygulama kilitlenirse veya hata ayıklama sırasında açılmazsa, bkz. [tam zamanında hata ayıklamayı giderme](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Windows kayıt defterinden tam zamanında hata ayıklamayı devre dışı bırak

Visual Studio artık bilgisayarınızda yüklü olmasa bile tam zamanında hata ayıklama hala etkinleştirilebilir. Visual Studio artık yüklenmemişse, Windows kayıt defterini düzenleyerek tam zamanında hata ayıklamayı devre dışı bırakabilirsiniz.

**Kayıt defterini düzenleyerek tam zamanında hata ayıklamayı devre dışı bırakmak için:**

1. Windows **başlat** menüsünde, **kayıt defteri düzenleyicisi 'ni** (*regedit.exe*) çalıştırın.

2. **Kayıt defteri Düzenleyicisi** penceresinde, aşağıdaki kayıt defteri girdilerini bulun ve silin:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\ . NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![JıT kayıt defteri anahtarı](../debugger/media/dbg-jit-registry.png "JIT kayıt defteri anahtarı")

3. Bilgisayarınızda 64 bitlik bir işletim sistemi çalışıyorsa, aşağıdaki kayıt defteri girdilerini de silin:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\ . NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Diğer kayıt defteri anahtarlarını sildiğinizden veya değiştirmediğinden emin olun.

5. **Kayıt defteri Düzenleyicisi** penceresini kapatın.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Windows formunda tam zamanında hata ayıklamayı etkinleştir

varsayılan olarak, Windows Form uygulamalarının kurtarabilmesi durumunda uygulamanın çalışmaya devam etmesini sağlayan en üst düzey bir özel durum işleyicisi vardır. Windows Forms bir uygulama işlenmeyen bir özel durum oluşturursa, şu iletişim kutusu görüntülenir:

![Windows İşlenmeyen özel durum formu](../debugger/media/windowsformsunhandledexception.png "Windows Form işsiz özel durumu")

standart Windows Form hata işleme yerine tam zamanında hata ayıklamayı etkinleştirmek için şu ayarları ekleyin:

- `system.windows.forms` *machine.config* veya *\<app name> . exe.config* dosyasının bölümünde, `jitDebugging` değeri şu şekilde ayarlayın `true` :

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- C++ Windows Form uygulamasında, `DebuggableAttribute` `true` bir *.config* dosyasında veya kodunuzda olarak da ayarlayın. [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) ile ve [/OG](/cpp/build/reference/og-global-optimizations)olmadan derlerseniz, derleyici bu özniteliği sizin için ayarlar. Ancak, en iyi duruma getirilmemiş bir yayın derlemesinde hata ayıklamak istiyorsanız, `DebuggableAttribute` uygulamanızın *AssemblyInfo. cpp* dosyasına aşağıdaki satırı ekleyerek ayarlamanız gerekir:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Daha fazla bilgi için bkz. <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Tam zamanında hata ayıklamayı kullan
Bu örnek, bir uygulama hata oluşturduğunda tam zamanında hata ayıklama işlemi boyunca size yol gösterir.

- bu adımları izlemek için Visual Studio yüklü olmalıdır. Visual Studio yoksa ücretsiz [Visual Studio Community sürümünü](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)indirebilirsiniz.

- **Araç** seçeneklerinde tam zamanında hata ayıklamanın [etkinleştirildiğinden](#BKMK_Enabling) emin olun  >    >    >  .

bu örnekte, bir [NullReferenceException](/dotnet/api/system.nullreferenceexception)oluşturan Visual Studio bir C# konsol uygulaması oluşturacaksınız.

1. Visual Studio ' de, ThrowsNullException adlı bir C# konsol uygulaması (**dosya**  >  **yeni**  >  **Project**  >  **Visual C#**  >  **konsol uygulaması**) oluşturun.  Visual Studio proje oluşturma hakkında daha fazla bilgi için bkz. [izlenecek yol: basit bir uygulama oluşturma](../get-started/csharp/tutorial-wpf.md).

1. proje Visual Studio açıldığında *Program. cs* dosyasını açın. Main () yöntemini bir satırı konsola yazdıran aşağıdaki kodla değiştirin ve ardından bir NullReferenceException şunu oluşturur:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Çözümü oluşturmak için, **Hata Ayıkla** (varsayılan) veya **Sürüm** yapılandırması ' nı seçin ve ardından **derleme**  >  **yeniden oluşturma çözümü**' nü seçin.

   > [!NOTE]
   > - Tam hata ayıklama deneyimi için **hata ayıklama** yapılandırması ' nı seçin.
   > - [Yayın](../debugger/how-to-set-debug-and-release-configurations.md) yapılandırması ' nı seçerseniz, bu yordamın çalışması için [yalnızca kendi kodum](../debugger/just-my-code.md) kapatmanız gerekir. **Araç**  >  **seçenekleri**  >  **hata ayıklama** altında **yalnızca kendi kodum etkinleştir** seçimini kaldırın.

   Derleme konfigürasyonları hakkında daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).

1. C# proje klasörünüzde (*. ..\ThrowsNullException\ThrowsNullException\bin\Debug* veya *. ..\ThrowsNullException\ThrowsNullException\bin\Release*) oluşturulan uygulama *ThrowsNullException.exe* açın.

   Aşağıdaki komut penceresini görmeniz gerekir:

   ![ThrowsNullException.exe için konsolun ekran görüntüsü, işlenmemiş bir null başvurusu özel durumu (System. NullReferenceException) oluşturur.](../debugger/media/throwsnullexceptionconsole.png)

1. **Tam zamanında hata ayıklayıcı Seç** iletişim kutusu açılır.

   ![ThrowsNullException.exe konsolu penceresinde özel durum görüntülendikten sonra görünen tam zamanında hata ayıklayıcı Seç iletişim kutusunun ekran görüntüsü.](../debugger/media/justintimedialog.png)

   **Kullanılabilir hata ayıklayıcılar** altında, henüz seçilmediyse **Yeni \<your preferred Visual Studio version/edition> örneği**' ni seçin.

1. **Tamam**’ı seçin.

   ThrowsNullException projesi Visual Studio yeni bir örneğinde açılır ve yürütme, özel durumu oluşturan satırda durdurulur:

   ![özel durumu oluşturan kaynak kodu satırı vurgulaması ile Visual Studio içindeki ThrowsNullException projesinin ekran görüntüsü.](../debugger/media/nullreferencesecondinstance.png)

Bu noktada hata ayıklamayı başlatabilirsiniz. Gerçek bir uygulamada hata ayıklaması yaptıysanız kodun özel durumu nasıl yayımladığına ilişkin bilgi almanız gerekir.

> [!CAUTION]
> Uygulamanız güvenilmeyen kod içeriyorsa, hata ayıklamaya devam edip etmeyeceğine karar vermenize olanak sağlayan bir güvenlik uyarısı iletişim kutusu görüntülenir. Hata ayıklamaya devam etmeden önce koda güvenip güvenmeyeceğinizi belirleyin. Kodu kendiniz yazdınız mı? Uygulama uzak bir makinede çalışıyorsa, işlemin adını tanıyor musunuz? Uygulama yerel olarak çalışıyorsa, bilgisayarınızda kötü amaçlı kod çalıştırma olasılığını göz önünde bulundurun. Kodun güvenilir olduğuna karar verirseniz **Tamam**' ı seçin. Aksi takdirde **iptal**' i seçin.

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Tam zamanında hata ayıklama sorunlarını giderme

Tam zamanında hata ayıklama bir uygulama kilitlenirse, Visual Studio ' de etkinleştirilse de başlamaz:

- Windows Hata Bildirimi bilgisayarınızdaki hata işleme üzerinden alınıyor.

  Bu sorunu onarmak için kayıt defteri Düzenleyicisi 'ni kullanarak, **Değer verisi** **1** olan **devre dışı** bir **DWORD değerini** aşağıdaki kayıt defteri anahtarlarına ekleyin:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  - (64 bit makineler için): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows Error Reporting**

  Daha fazla bilgi için bkz [.. WER ayarları](/windows/desktop/wer/wer-settings).

- bilinen bir Windows sorunu, tam zamanında hata ayıklayıcının başarısız olmasına neden olabilir.

  Bu, aşağıdaki kayıt defteri anahtarlarına **1** **değerli verileri** içeren **Auto** **DWORD değeri** eklemektir:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (64 bit makineler için): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Anında hata ayıklama sırasında aşağıdaki hata iletilerini görebilirsiniz:

- **Kilitlenen işleme iliştirilemiyor. belirtilen program bir Windows veya MS-DOS programı değil.**

    Hata ayıklayıcı, başka bir kullanıcı altında çalışan bir işleme iliştirmeye çalıştı.

    bu sorunu geçici olarak çözmek için Visual Studio, **hata ayıklama**  >  **iliştirme işlemini** açın (veya **Ctrl**  +  **Alt**  +  **P** tuşlarına basın) ve **kullanılabilir işlemler** listesinde hata ayıklamak istediğiniz işlemi bulun. işlemin adını görmüyorsanız, **Visual Studio tam zamanında hata ayıklayıcı** iletişim kutusunda işlem kimliğini bulun. **Kullanılabilir işlemler** listesinde işlemi seçin ve **Ekle**' yi seçin. Tam zamanında hata ayıklayıcı iletişim kutusunu kapatmak için **Hayır** ' ı seçin.

- **Hiçbir Kullanıcı oturum açmamış olduğundan hata ayıklayıcı başlatılamadı.**

    Konsolda oturum açmış bir kullanıcı yok, bu nedenle tam zamanında hata ayıklama iletişim kutusunu görüntüleyecek Kullanıcı oturumu yok.

    Bu sorunu gidermek için makinede oturum açın.

- **Sınıf kayıtlı değil.**

    Hata ayıklayıcısı büyük olasılıkla bir yükleme sorunu nedeniyle kayıtlı değil bir COM sınıfı oluşturma denemesi yaptı.

    Bu sorunu düzeltmek için, Visual Studio Yükleyicisi yüklemenizi yeniden yüklemek veya onarmak Visual Studio kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Seçenekler, Hata Ayıklama, Tam Zamanında iletişim kutusu](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu bir işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme ekleme](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
