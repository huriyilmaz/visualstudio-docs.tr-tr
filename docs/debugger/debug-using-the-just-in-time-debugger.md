---
title: Tam zamanında hata ayıklayıcı kullanarak hata ayıklayın | Microsoft Docs
ms.date: 09/24/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b842fa4ce7c75e061a58d980cefe5648094c2ef7
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188674"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Visual Studio 'da tam zamanında hata ayıklayıcı kullanarak hata ayıklayın

Visual Studio hataları dışında çalışan bir uygulama olduğunda veya kilitlenirse, tam zamanında hata ayıklama Visual Studio 'Yu otomatik olarak başlatabilir. Tam zamanında hata ayıklama sayesinde, uygulamaları Visual Studio dışında test edebilir ve bir sorun oluştuğunda hata ayıklamaya başlamak için Visual Studio 'Yu açabilirsiniz.

Tam zamanında hata ayıklama Windows Masaüstü uygulamaları için geçerlidir. Evrensel Windows uygulamaları veya Görselleştiriciler gibi yerel bir uygulamada barındırılan yönetilen kod için çalışmaz.

> [!TIP]
> Yalnızca tam zamanında hata ayıklayıcı iletişim kutusunun görüntülenmesini durdurmak istiyorsanız ancak Visual Studio yüklü değilse, [tam zamanında hata ayıklayıcıyı devre dışı bırakma](../debugger/just-in-time-debugging-in-visual-studio.md)konusuna bakın. Visual Studio yüklüyse, [Windows kayıt defterinden tam zamanında hata ayıklamayı devre dışı bırakmanız](#disable-just-in-time-debugging-from-the-windows-registry)gerekebilir.

## <a name="BKMK_Enabling"></a>Visual Studio 'da tam zamanında hata ayıklamayı etkinleştirme veya devre dışı bırakma

>[!NOTE]
>Tam zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak için, Visual Studio 'Yu yönetici olarak çalıştırıyor olmanız gerekir. Tam zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak bir kayıt defteri anahtarı ayarlar ve bu anahtarı değiştirmek için yönetici ayrıcalıkları gerekebilir. Visual Studio 'Yu yönetici olarak açmak için, Visual Studio uygulamasına sağ tıklayın ve **yönetici olarak çalıştır**' ı seçin.

Visual Studio **araçları** > **Seçenekler** (veya **hata ayıklama** > **seçenekleri**) iletişim kutusundan tam zamanında hata ayıklamayı yapılandırabilirsiniz.

**Tam zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak için:**

1. **Araçlar** veya **Hata Ayıkla** menüsünde, **Seçenekler** > **hata ayıklama** > **tam zamanında**seçeneğini belirleyin.

   ![JıT hata ayıklamayı etkinleştirme veya devre dışı bırakma](../debugger/media/dbg-jit-enable-or-disable.png "JıT hata ayıklamayı etkinleştirme veya devre dışı bırakma")

1. **Bu kod türleri Için tam zamanında hata ayıklamayı etkinleştir** kutusunda hata ayıklamada tam zamanında hata ayıklamayı istediğiniz kod türlerini seçin: **yönetilen**, **Yerel**ve/veya **betiği**.

1. **Tamam ' ı**seçin.

Just-In-Time hata ayıklayıcıyı etkinleştirirseniz, ancak bir uygulama kilitlenirse veya hata ayıklama sırasında açılmazsa, bkz. [tam zamanında hata ayıklamayı giderme](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Windows kayıt defterinden tam zamanında hata ayıklamayı devre dışı bırak

Visual Studio artık bilgisayarınızda yüklü olmasa bile tam zamanında hata ayıklama hala etkinleştirilebilir. Visual Studio artık yüklü değilse, Windows kayıt defterini düzenleyerek tam zamanında hata ayıklamayı devre dışı bırakabilirsiniz.

**Kayıt defterini düzenleyerek tam zamanında hata ayıklamayı devre dışı bırakmak için:**

1. Windows **Başlat** menüsünde **kayıt defteri Düzenleyicisi 'ni** (*Regedit. exe*) çalıştırın.

2. **Kayıt defteri Düzenleyicisi** penceresinde, aşağıdaki kayıt defteri girdilerini bulun ve silin:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![JıT kayıt defteri anahtarı](../debugger/media/dbg-jit-registry.png "JıT kayıt defteri anahtarı")

3. Bilgisayarınızda 64 bitlik bir işletim sistemi çalışıyorsa, aşağıdaki kayıt defteri girdilerini de silin:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Diğer kayıt defteri anahtarlarını sildiğinizden veya değiştirmediğinden emin olun.

5. **Kayıt defteri Düzenleyicisi** penceresini kapatın.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Bir Windows formunda tam zamanında hata ayıklamayı etkinleştir

Varsayılan olarak, Windows form uygulamalarının kurtarabilmesi durumunda uygulamanın çalışmaya devam etmesini sağlayan bir üst düzey özel durum işleyicisi vardır. Windows Forms bir uygulama işlenmeyen bir özel durum oluşturursa, şu iletişim kutusu görüntülenir:

![Windows formu işlenmeyen özel durum](../debugger/media/windowsformsunhandledexception.png "Windows formu işlenmeyen özel durum")

Standart Windows form hatası işleme yerine tam zamanında hata ayıklamayı etkinleştirmek için şu ayarları ekleyin:

- *Machine. config* veya *\<uygulama adı >. exe. config* dosyasının `system.windows.forms` bölümünde `jitDebugging` değerini `true`olarak ayarlayın:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- Bir C++ Windows form uygulamasında, bir *. config* dosyasında veya kodunuzda`true``DebuggableAttribute`de ayarlayın. [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) ile ve [/OG](/cpp/build/reference/og-global-optimizations)olmadan derlerseniz, derleyici bu özniteliği sizin için ayarlar. Ancak, en iyi duruma getirilmemiş bir yayın derlemesinde hata ayıklamak istiyorsanız, uygulamanızın *AssemblyInfo. cpp* dosyasına aşağıdaki satırı ekleyerek `DebuggableAttribute` ayarlamanız gerekir:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Daha fazla bilgi için bkz. <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="BKMK_Using_JIT"></a>Tam zamanında hata ayıklamayı kullan
Bu örnek, bir uygulama hata oluşturduğunda tam zamanında hata ayıklama işlemi boyunca size yol gösterir.

- Bu adımları izlemek için Visual Studio yüklü olmalıdır. Visual Studio yoksa, ücretsiz [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)'ı indirebilirsiniz.

- **Araç** > **seçeneklerinde** tam zamanında hata ayıklamanın [etkinleştirildiğinden](#BKMK_Enabling) emin olun > **hata ayıklama** > **tam zamanında**.

Bu örnekte, Visual Studio 'da bir C# [NullReferenceException](/dotnet/api/system.nullreferenceexception)' i oluşturan bir konsol uygulaması oluşturacaksınız.

1. Visual Studio 'da, *ThrowsNullException*adlı C# bir konsol uygulaması (**Dosya** > **Yeni** > **Proje** >  **C# Visual** > **konsol uygulaması**) oluşturun. Visual Studio 'da proje oluşturma hakkında daha fazla bilgi için bkz. [Izlenecek yol: basit bir uygulama oluşturma](../get-started/csharp/tutorial-wpf.md).

1. Proje Visual Studio 'da açıldığında, *program.cs* dosyasını açın. Main () yöntemini bir satırı konsola yazdıran aşağıdaki kodla değiştirin ve ardından bir NullReferenceException şunu oluşturur:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Çözümü oluşturmak için, **hata ayıklama** (varsayılan) veya **Sürüm** yapılandırması ' nı seçin ve ardından **Yapı** > **yeniden oluştur**' u seçin.

   > [!NOTE]
   > - Tam hata ayıklama deneyimi için **hata ayıklama** yapılandırması ' nı seçin.
   > - [Yayın](../debugger/how-to-set-debug-and-release-configurations.md) yapılandırması ' nı seçerseniz, bu yordamın çalışması için [yalnızca kendi kodum](../debugger/just-my-code.md) kapatmanız gerekir. **Araçlar** > **Seçenekler** > **hata ayıklama**altında **yalnızca kendi kodum etkinleştir**' i kaldırın.

   Derleme konfigürasyonları hakkında daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).

1. Oluşturulan app *ThrowsNullException. exe* ' yi C# proje klasörünüzde ( *. .\ThrowsNullException\ThrowsNullException\bin\Debug* veya *. .\ThrowsNullException\ThrowsNullException\bin\Release*) açın.

   Aşağıdaki komut penceresini görmeniz gerekir:

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. **Tam zamanında hata ayıklayıcı Seç** iletişim kutusu açılır.

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   **Kullanılabilir hata ayıklayıcılar**' ın altında, **tercih edilen Visual Studio sürümünüz \<yeni örneği**' ni seçin, zaten seçili değilse >.

1. **Tamam ' ı**seçin.

   ThrowsNullException projesi Visual Studio 'nun yeni bir örneğinde açılarak yürütme, özel durumu oluşturan satırda durdurulur:

   ![Nullreferencesecondınstance](../debugger/media/nullreferencesecondinstance.png "Nullreferencesecondınstance")

Bu noktada hata ayıklamayı başlatabilirsiniz. Gerçek bir uygulamada hata ayıklaması yaptıysanız kodun özel durumu nasıl yayımladığına ilişkin bilgi almanız gerekir.

> [!CAUTION]
> Uygulamanız güvenilmeyen kod içeriyorsa, hata ayıklamaya devam edip etmeyeceğine karar vermenize olanak sağlayan bir güvenlik uyarısı iletişim kutusu görüntülenir. Hata ayıklamaya devam etmeden önce koda güvenip güvenmeyeceğinizi belirleyin. Kodu kendiniz yazdınız mı? Uygulama uzak bir makinede çalışıyorsa, işlemin adını tanıyor musunuz? Uygulama yerel olarak çalışıyorsa, bilgisayarınızda kötü amaçlı kod çalıştırma olasılığını göz önünde bulundurun. Kodun güvenilir olduğuna karar verirseniz **Tamam**' ı seçin. Aksi takdirde **iptal**' i seçin.

## <a name="jit_errors"></a>Tam zamanında hata ayıklama sorunlarını giderme

Visual Studio 'da etkinleştirilmiş olsa bile, bir uygulama kilitlenirse tam zamanında hata ayıklama başlamadığında:

- Windows Hata Bildirimi bilgisayarınızdaki hata işleme üzerinden alınıyor.

  Bu sorunu onarmak için kayıt defteri Düzenleyicisi 'ni kullanarak, **Değer verisi** **1**olan **devre dışı**bir **DWORD değerini** aşağıdaki kayıt defteri anahtarlarına ekleyin:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows hata bildirimi**

  - (64 bit makineler için): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows hata raporlama**

  Daha fazla bilgi için bkz [. WER ayarları](/windows/desktop/wer/wer-settings).

- Bilinen bir Windows sorunu, tam zamanında hata ayıklayıcının başarısız olmasına neden olabilir.

  Bu, aşağıdaki kayıt defteri anahtarlarına **1** **değerli verileri** içeren **Auto** **DWORD değeri** eklemektir:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (64 bit makineler için): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Anında hata ayıklama sırasında aşağıdaki hata iletilerini görebilirsiniz:

- **Kilitlenen işleme iliştirilemiyor. Belirtilen program bir Windows veya MS-DOS programı değil.**

    Hata ayıklayıcı, başka bir kullanıcı altında çalışan bir işleme iliştirmeye çalıştı.

    Bu sorunu geçici olarak çözmek için, Visual Studio 'da **hata ayıkla** > **İşleme İliştir**' i açın ve **kullanılabilir işlemler** listesinde hata ayıklamak istediğiniz işlemi bulun. İşlemin adını bilmiyor değilseniz, **Visual Studio tam zamanında hata ayıklayıcı** Iletişim kutusunda işlem kimliği ' ni bulun. **Kullanılabilir işlemler** listesinde işlemi seçin ve **Ekle**' yi seçin. Tam zamanında hata ayıklayıcı iletişim kutusunu kapatmak için **Hayır** ' ı seçin.

- **Hiçbir Kullanıcı oturum açmamış olduğundan hata ayıklayıcı başlatılamadı.**

    Konsolda oturum açmış bir kullanıcı yok, bu nedenle tam zamanında hata ayıklama iletişim kutusunu görüntüleyecek Kullanıcı oturumu yok.

    Bu sorunu gidermek için makinede oturum açın.

- **Sınıf kayıtlı değil.**

    Hata ayıklayıcı, muhtemelen bir yükleme sorunu nedeniyle kayıtlı olmayan bir COM sınıfı oluşturmayı denedi.

    Bu sorunu gidermek için Visual Studio Yükleyicisi kullanarak Visual Studio yüklemenizi yeniden yükleyin veya onarın.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Seçenekler, hata ayıklama, tam zamanında iletişim kutusu](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Güvenlik Uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme eklemeyin](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
