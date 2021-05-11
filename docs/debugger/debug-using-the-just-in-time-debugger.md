---
title: Tam Zamanında Hata Ayıklayıcısını kullanarak hata ayıklama | Microsoft Docs
description: Visual Studio'de Tam Zamanında Hata Ayıklayıcı'Visual Studio. Tam Zamanında hata ayıklama, bir uygulama Visual Studio kilitlenirse otomatik olarak başlatabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 09/24/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3bdd35056706491ace6e5e6b2f7c3f6a45464d2e
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729253"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Visual Studio'de Tam Zamanında Hata Ayıklayıcı kullanarak hata Visual Studio

Tam Zamanında hata ayıklama, uygulamanın dışında Visual Studio veya kilitlenmesi Visual Studio otomatik olarak başlatabilirsiniz. Tam Zamanında hata ayıklama ile uygulamaları uygulamanın dışında test Visual Studio ve bir sorun Visual Studio hata ayıklamaya başlamak için uygulamaları açabilirsiniz.

Tam Zamanında hata ayıklama, Windows masaüstü uygulamaları için çalışır. Evrensel Windows Uygulamaları veya Görselleştiriciler gibi yerel bir uygulamada barındırılan yönetilen kod için çalışmaz.

> [!TIP]
> Tam Zamanında Hata Ayıklayıcı iletişim kutusunun görünmesini durdurmak ancak henüz yüklü Visual Studio durdurmak için bkz. Tam Zamanında Hata [Ayıklayıcı'sını devre dışı bırakma.](../debugger/just-in-time-debugging-in-visual-studio.md) Daha önce yükleme Visual Studio, Windows kayıt defterinden Tam Zamanında hata ayıklamayı [devre dışı bırakmanız gerekir.](#disable-just-in-time-debugging-from-the-windows-registry)

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a> Uygulama içinde Tam Zamanında hata ayıklamayı etkinleştirme veya devre dışı Visual Studio

>[!NOTE]
>Tam Zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak için yönetici olarak Visual Studio çalıştırmanız gerekir. Tam Zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak bir kayıt defteri anahtarı ayarlar ve bu anahtarı değiştirmek için yönetici ayrıcalıkları gerekebilir. Yönetici olarak Visual Studio açmak için, uygulamanın Visual Studio tıklayın ve Yönetici olarak **çalıştır'ı seçin.**

Tam Zamanında hata ayıklamayı Visual Studio Araçları Seçenekleri   >   (veya Hata Ayıklama Seçenekleri ) iletişim   >  **kutusundan** yapılandırabilirsiniz.

**Tam Zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak için:**

1. Araçlar veya **Hata** **Ayıklama menüsünde** Seçenekler Hata **Ayıklama**  >  **Tam Zamanında** seçeneğini  >  **belirleyin.**

   ![JIT hata ayıklamayı etkinleştirme veya devre dışı bırakma](../debugger/media/dbg-jit-enable-or-disable.png "JIT hata ayıklamayı etkinleştirme veya devre dışı bırakma")

1. Bu **kod türleri için** Tam Zamanında hata ayıklamayı etkinleştir kutusunda, Hata ayıklamanın Tam Zamanında hata ayıklamasını istediğiniz kod türlerini seçin: **Yönetilen,** Yerel **ve/veya** **Betik**.

1. **Tamam**’ı seçin.

Just-In-Time hata ayıklayıcıyı etkinleştirirseniz, ancak bir uygulama kilitlenirse veya hata ayıklama sırasında açılmazsa, bkz. [tam zamanında hata ayıklamayı giderme](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Windows kayıt defterinden tam zamanında hata ayıklamayı devre dışı bırak

Visual Studio artık bilgisayarınızda yüklü olmasa bile tam zamanında hata ayıklama hala etkinleştirilebilir. Visual Studio artık yüklü değilse, Windows kayıt defterini düzenleyerek tam zamanında hata ayıklamayı devre dışı bırakabilirsiniz.

**Kayıt defterini düzenleyerek tam zamanında hata ayıklamayı devre dışı bırakmak için:**

1. Windows **Başlat** menüsünde, **kayıt defteri düzenleyicisi 'ni** (*regedit.exe*) çalıştırın.

2. **Kayıt defteri Düzenleyicisi** penceresinde, aşağıdaki kayıt defteri girdilerini bulun ve silin:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\ . NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![JıT kayıt defteri anahtarı](../debugger/media/dbg-jit-registry.png "JIT kayıt defteri anahtarı")

3. Bilgisayarınızda 64 bitlik bir işletim sistemi çalışıyorsa, aşağıdaki kayıt defteri girdilerini de silin:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\ . NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Diğer kayıt defteri anahtarlarını sildiğinizden veya değiştirmediğinden emin olun.

5. **Kayıt defteri Düzenleyicisi** penceresini kapatın.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Bir Windows formunda tam zamanında hata ayıklamayı etkinleştir

Varsayılan olarak, Windows form uygulamalarının kurtarabilmesi durumunda uygulamanın çalışmaya devam etmesini sağlayan bir üst düzey özel durum işleyicisi vardır. Windows Forms bir uygulama işlenmeyen bir özel durum oluşturursa, şu iletişim kutusu görüntülenir:

![Windows formu işlenmeyen özel durum](../debugger/media/windowsformsunhandledexception.png "Windows Formu işlanmamış özel durumu")

Standart Windows form hatası işleme yerine tam zamanında hata ayıklamayı etkinleştirmek için şu ayarları ekleyin:

- Dosyanın `system.windows.forms`machine.config *\<app name>.exe.config* değerini `jitDebugging` olarak `true` ayarlayın:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- Bir C++ Windows Form uygulamasında, bir `DebuggableAttribute` `true` *.config* dosyasında veya kodunda olarak da ayarlayın. [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) ile ve [/Og](/cpp/build/reference/og-global-optimizations)olmadan derlersanız, derleyici bu özniteliği sizin için ayarlar. Ancak, en iyi duruma getirilmiş olmayan bir yayın derlemesinde hata ayıklamak için, aşağıdaki satırı `DebuggableAttribute` *uygulamanın AssemblyInfo.cpp* dosyasına ekleyerek ayarlamanız gerekir:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Daha fazla bilgi için bkz. <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Tam Zamanında hata ayıklamayı kullanma
Bu örnek, bir uygulama hata atarken Tam Zamanında hata ayıklamada size yol gösterir.

- Bu adımları Visual Studio için yüklü olması gerekir. Herhangi bir sürüme sahip Visual Studio ücretsiz Visual Studio Community [indirebilirsiniz.](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)

- Araç Seçenekleri Tam Zamanında Hata [](#BKMK_Enabling) Ayıklama içinde Tam Zamanında  >    >  **hata ayıklamanın**  >  **etkinleştirildiğinden emin olun.**

Bu örnekte, bir [NullReferenceException](/dotnet/api/system.nullreferenceexception)Visual Studio bir C# konsol uygulaması yapacaksınız.

1. Bu Visual Studio  >    >    >    >   *ThrowsNullException* adlı bir C# konsol uygulaması ( Dosya Yeni Proje Visual C# Konsol Uygulaması ) oluşturun. Uygulama içinde proje oluşturma hakkında daha fazla Visual Studio için bkz. [Kılavuz: Basit bir uygulama oluşturma.](../get-started/csharp/tutorial-wpf.md)

1. Proje Visual Studio *Program.cs dosyasını* açın. Main() yöntemini konsola bir satır yazdıran ve nullReferenceException döndüren aşağıdaki kodla değiştirin:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Çözümü derlemek için Hata  Ayıklama (varsayılan) veya Yayın **yapılandırmasını** seçin ve ardından Çözümü Yeniden   >  **Derleme'yi seçin.**

   > [!NOTE]
   > - Tam **hata ayıklama deneyimi** için Hata ayıklama yapılandırması'nın seçin.
   > - Yayın [yapılandırması'nın](../debugger/how-to-set-debug-and-release-configurations.md) seçerek bu [yordamın Yalnızca kendi kodum](../debugger/just-my-code.md) için yapılandırmayı kapatmanız gerekir. Araç **Seçenekleri Hata**  >  **Ayıklama**  >  **altında,** Etkinleştir'in seçimini **Yalnızca kendi kodum.**

   Derleme yapılandırmaları hakkında daha fazla bilgi için [bkz. Derleme yapılandırmalarını anlama.](../ide/understanding-build-configurations.md)

1. C# proje *ThrowsNullException.exe* (*...\ThrowsNullException\ThrowsNullException\bin\Debug* veya *...\ThrowsNullException\ThrowsNullException\bin\Release*) yerleşik uygulama klasörünü açın.

   Aşağıdaki komut penceresini görüyor gerekir:

   ![İşlanmamış null başvuru özel durumu (System.NullReferenceException) ThrowsNullException.exe için konsol ekran görüntüsü.](../debugger/media/throwsnullexceptionconsole.png)

1. Tam **Zamanında Hata Ayıklayıcı Seç iletişim** kutusu açılır.

   ![Özel durum konsol penceresinde görüntülendiğinde görüntülenen Tam Zamanında Hata Ayıklayıcısı iletişim kutusunun ekran ThrowsNullException.exe görüntüsü.](../debugger/media/justintimedialog.png)

   Kullanılabilir **Hata Ayıklayıcılar'ın** **altında, henüz seçilmemişse \<your preferred Visual Studio version/edition>** Yeni örneği 'yi seçin.

1. **Tamam**’ı seçin.

   ThrowsNullException projesi yeni bir Visual Studio içinde açılır ve yürütme özel durumuna neden olan satırda durdurulur:

   ![Visual Studio'de ThrowsNullException projesinin ekran görüntüsü, özel durumu öne alan kaynak kod satırı vurgulanmış.](../debugger/media/nullreferencesecondinstance.png)

Bu noktada hata ayıklamaya başlayabilirsiniz. Gerçek bir uygulamada hata ayıklaması yaptıysanız, kodun neden özel durumu atıyor olduğunu bulmalıyabilirsiniz.

> [!CAUTION]
> Uygulamanız güvenilmeyen kod içeriyorsa, hata ayıklamaya devam edip edemeyenlere karar vermenizi sağlayan bir güvenlik uyarısı iletişim kutusu görüntülenir. Hata ayıklamaya devam etmek için koda güvenip güvenmey karar verin. Kodu kendiniz mi yazdınız? Uygulama uzak bir makinede çalışıyorsa, sürecin adını tanıyor musunuz? Uygulama yerel olarak çalışıyorsa, bilgisayarınızda kötü amaçlı kod çalıştırma olasılığını göz önünde bulundurabilirsiniz. Kodun güvenilir olduğuna karar veriyorsanız Tamam'ı **seçin.** Aksi takdirde **İptal'i seçin.**

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Tam Zamanında hata ayıklama sorunlarını giderme

Uygulama şu anda etkin olsa da bir uygulama kilitleniyorsa tam zamanında hata ayıklama Visual Studio:

- Windows Hata Bildirimi bilgisayarınızdaki hata işleme üzerinden alınıyor.

  Bu sorunu onarmak için kayıt defteri Düzenleyicisi 'ni kullanarak, **Değer verisi** **1** olan **devre dışı** bir **DWORD değerini** aşağıdaki kayıt defteri anahtarlarına ekleyin:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  - (64 bit makineler için): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows Error Reporting**

  Daha fazla bilgi için bkz [.. WER ayarları](/windows/desktop/wer/wer-settings).

- Bilinen bir Windows sorunu, tam zamanında hata ayıklayıcının başarısız olmasına neden olabilir.

  Bu, aşağıdaki kayıt defteri anahtarlarına **1** **değerli verileri** içeren **Auto** **DWORD değeri** eklemektir:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (64 bit makineler için): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Anında hata ayıklama sırasında aşağıdaki hata iletilerini görebilirsiniz:

- **Kilitlenen işleme iliştirilemiyor. Belirtilen program bir Windows veya MS-DOS programı değil.**

    Hata ayıklayıcı, başka bir kullanıcı altında çalışan bir işleme iliştirmeye çalıştı.

    Bu sorunu geçici olarak çözmek için, Visual Studio 'da **hata ayıklama**  >  **iliştirme işlemini** açın (veya **CTRL**  +  **alt**  +  **P** tuşlarına basın) ve **kullanılabilir işlemler** listesinde hata ayıklamak istediğiniz işlemi bulun. İşlemin adını bilmiyor değilseniz, **Visual Studio tam zamanında hata ayıklayıcı** Iletişim kutusunda işlem kimliği ' ni bulun. **Kullanılabilir işlemler** listesinde işlemi seçin ve **Ekle**' yi seçin. Tam zamanında hata ayıklayıcı iletişim kutusunu kapatmak için **Hayır** ' ı seçin.

- **Hiçbir Kullanıcı oturum açmamış olduğundan hata ayıklayıcı başlatılamadı.**

    Konsolda oturum açmış bir kullanıcı yok, bu nedenle tam zamanında hata ayıklama iletişim kutusunu görüntüleyecek Kullanıcı oturumu yok.

    Bu sorunu gidermek için makinede oturum açın.

- **Sınıf kayıtlı değil.**

    Hata ayıklayıcısı büyük olasılıkla bir yükleme sorunu nedeniyle kayıtlı değil bir COM sınıfı oluşturma denemesi yaptı.

    Bu sorunu çözmek için, Visual Studio Yükleyicisi yüklemenizi yeniden yüklemek veya onarmak için Visual Studio kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Seçenekler, Hata Ayıklama, Tam Zamanında iletişim kutusu](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu bir işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz bu işleme ekleme](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
