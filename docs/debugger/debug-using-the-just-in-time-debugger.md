---
title: Tam Zamanında Hata Ayıklayıcı hata ayıklayıcısını kullanarak hata | Microsoft Docs
description: Visual Studio'de Tam Zamanında Hata Ayıklayıcı'Visual Studio. Tam Zamanında hata ayıklama, uygulama Visual Studio kilitlenirse otomatik olarak başlatabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 12/20/2021
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
ms.openlocfilehash: b3930e0348f2cb671b7f9392af5ee0ef1e9b7a97
ms.sourcegitcommit: 52a425b5a541034cda26db8df9cd43281c007e80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2021
ms.locfileid: "135540681"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Visual Studio'de Tam Zamanında Hata Ayıklayıcı kullanarak hata Visual Studio

Tam Zamanında hata ayıklama, uygulamanın dışında Visual Studio veya kilitlenmesi Visual Studio otomatik olarak başlatabilirsiniz. Tam Zamanında hata ayıklama ile uygulamaları uygulamanın dışında test Visual Studio ve bir sorun Visual Studio hata ayıklamaya başlamak için uygulamaları açabilirsiniz.

Tam Zamanında hata ayıklama, masaüstü Windows çalışır. Universal Windows Apps veya Görselleştiriciler gibi yerel bir uygulamada barındırılan yönetilen kod için çalışmaz.

> [!TIP]
> Yalnızca Tam Zamanında Hata Ayıklayıcı iletişim kutusunun görünmesini durdurmak ancak henüz yüklü Visual Studio istemiyorsanız, bkz. Tam Zamanında Hata [Ayıklayıcı'sını devre dışı bırakma.](../debugger/just-in-time-debugging-in-visual-studio.md) Daha önce yükleme Visual Studio, kayıt defterinden Tam Zamanında hata ayıklamayı [devre dışı bırakmanız Windows olabilir.](#disable-just-in-time-debugging-from-the-windows-registry)

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a>Uygulama içinde Tam Zamanında hata ayıklamayı etkinleştirme veya devre dışı Visual Studio

>[!NOTE]
>Tam Zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak için yönetici olarak Visual Studio çalıştırmanız gerekir. Tam Zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak bir kayıt defteri anahtarı ayarlar ve bu anahtarı değiştirmek için yönetici ayrıcalıkları gerekebilir. Yönetici olarak Visual Studio açmak için, uygulamanın Visual Studio tıklayın ve Yönetici olarak **çalıştır'ı seçin.**

Tam Zamanında hata ayıklamayı Visual Studio Araçları Seçenekleri (veya Hata   >   Ayıklama Seçenekleri )   >  **iletişim kutusundan** yapılandırabilirsiniz.

**Tam Zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak için:**

1. Araçlar veya **Hata** **Ayıklama menüsünde** Seçenekler Hata **Ayıklama**  >  **Tam Zamanında** seçeneğini  >  **belirleyin.**

   ![JIT hata ayıklamayı etkinleştirme veya devre dışı bırakma](../debugger/media/dbg-jit-enable-or-disable.png "JIT hata ayıklamayı etkinleştirme veya devre dışı bırakma")

1. Bu **kod türleri için** Tam Zamanında hata ayıklamayı etkinleştir kutusunda, Tam Zamanında hata ayıklamanın hata ayıklamasını istediğiniz kod türlerini seçin: **Yönetilen,** Yerel **ve/veya** **Betik**.

1. **Tamam**’ı seçin.

Tam Zamanında hata ayıklayıcısını etkinleştirir ancak bir uygulama kilitleniyor veya hatalar olduğunda açılmazsa, bkz. Tam Zamanında hata [ayıklama sorunlarını giderme.](#jit_errors)

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Kayıt defterinden Tam Zamanında hata ayıklamayı Windows devre dışı bırakma

Tam Zamanında hata ayıklama, bilgisayarınızda artık yüklü Visual Studio bile etkinleştirilebilir. Bir Visual Studio artık yüklü değilse, kayıt defterini düzenleyerek Tam Zamanında hata ayıklamayı Windows.

**Kayıt defterini düzenleyerek Tam Zamanında hata ayıklamayı devre dışı bırakmak için:**

1. Başlangıç Windows **Kayıt Defteri** **Düzenleyicisi'ni** *(* regedit.exe).

2. 64 bit **bilgisayarlar** için Kayıt Defteri Düzenleyicisi penceresinde aşağıdaki kayıt defteri girdilerini bulun ve silin:

    - **\\HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft. NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    :::image type="content" source="../debugger/media/dbg-jit-registry.png" alt-text="JIT kayıt defteri anahtarı" border="true":::

3. Aşağıdaki kayıt defteri girdileri varsa veya bilgisayarınız 32 bit işletim sistemi çalıştırıyorsa aşağıdaki girdileri silin:

    - **\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft. NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Diğer kayıt defteri anahtarlarını silmeyi veya değiştirmeyin.

4. Kayıt Defteri **Düzenleyicisi penceresini** kapatın.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Bir Form Için Tam Zamanında hata ayıklamayı Windows etkinleştirme

Varsayılan olarak, Windows Form uygulamalarının kurtarılabilirse, uygulamanın çalışmaya devam sini sağlayan bir üst düzey özel durum işleyicisi vardır. Bir Windows Forms uygulaması işlanmamış bir özel durum oluşturursa aşağıdaki iletişim kutusu görüntülenir:

![Windows Form işsiz özel durumu](../debugger/media/windowsformsunhandledexception.png "Windows Form işsiz özel durumu")

Standart Form hata işleme yerine Tam Zamanında hata ayıklamayı Windows için şu ayarları ekleyin:

- machine.config`system.windows.forms` *\<app name> veya .exe.config* dosyasının bölümünde değerini olarak  `jitDebugging` `true` ayarlayın:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- C++ Windows Form uygulamasında, bir.config`DebuggableAttribute` `true` dosyasında  veya kodunda olarak ayarlayın. [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) ile ve [/Og](/cpp/build/reference/og-global-optimizations)olmadan derlersanız, derleyici bu özniteliği sizin için ayarlar. Ancak, en iyi duruma getirilmiş olmayan bir yayın derlemesinde hata ayıklamak için, aşağıdaki satırı `DebuggableAttribute` *uygulamanın AssemblyInfo.cpp* dosyasına ekleyerek ayarlamanız gerekir:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Daha fazla bilgi için bkz. <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Tam Zamanında hata ayıklamayı kullanma

Bu örnek, bir uygulama hata atarken Tam Zamanında hata ayıklamada size yol gösterir.

- Bu adımları Visual Studio yüklü olması gerekir. Visual Studio Visual Studio Community [indirebilirsiniz.](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)

- Araç Seçenekleri Tam Zamanında Hata [](#BKMK_Enabling) Ayıklama içinde Tam Zamanında  >    >  **hata ayıklamanın**  >  **etkinleştirildiğinden emin olun.**

Bu örnekte, bir [NullReferenceException](/dotnet/api/system.nullreferenceexception)Visual Studio bir C# konsol uygulaması yapacaksınız.

1. Bu  >    >    >    >   *Visual Studio, ThrowsNullException* adlı bir C# Project uygulaması ( Dosya Yeni Dosya Visual C# Konsol Uygulaması ) oluşturun. Uygulama içinde proje oluşturma hakkında daha fazla Visual Studio için bkz. [Adım adım kılavuz: Basit bir uygulama oluşturma.](../get-started/csharp/tutorial-wpf.md)

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

   ![İşlenemeyen null başvuru özel durumu (System.NullReferenceException) ThrowsNullException.exe için konsol ekran görüntüsü.](../debugger/media/throws-null-exception-console.png)

1. Tam **Zamanında Hata Ayıklayıcı Seç iletişim** kutusu açılır.

   ![Özel durum konsol penceresinde görüntülendiğinde görüntülenen Tam Zamanında Hata Ayıklayıcısı iletişim kutusunun ekran ThrowsNullException.exe görüntüsü.](../debugger/media/justintimedialog.png)

   Kullanılabilir **Hata Ayıklayıcılar'ın** **altında Yeni örneği'ne \<your preferred Visual Studio version/edition>**(henüz seçilmemişse) öğesini seçin.

1. **Tamam**’ı seçin.

   ThrowsNullException projesi yeni bir Visual Studio örneğinde açılır ve yürütme özel durumuna neden olan satırda durdurulur:

   ![Visual Studio'da ThrowsNullException projesinin ekran görüntüsü, özel durumu öne alan kaynak kod satırı vurgulanmış.](../debugger/media/null-reference-second-instance.png)

Bu noktada hata ayıklamaya başlayabilirsiniz. Gerçek bir uygulamada hata ayıklaması yaptıysanız, kodun neden özel durumu atıyor olduğunu bulmalıyabilirsiniz.

> [!CAUTION]
> Uygulamanız güvenilmeyen kod içeriyorsa, hata ayıklamaya devam edip edemeyenlere karar vermenizi sağlayan bir güvenlik uyarısı iletişim kutusu görüntülenir. Hata ayıklamaya devam etmek için koda güvenip güvenmey karar verin. Kodu kendiniz mi yazdınız? Uygulama uzak bir makinede çalışıyorsa, sürecin adını tanıyor musunuz? Uygulama yerel olarak çalışıyorsa, bilgisayarınızda kötü amaçlı kod çalıştırma olasılığını göz önünde bulundurabilirsiniz. Kodun güvenilir olduğuna karar veriyorsanız Tamam'ı **seçin.** Aksi takdirde **İptal'i seçin.**

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Tam Zamanında hata ayıklama sorunlarını giderme

Uygulamanın kilitlenmesi, uygulamada etkinleştirilse bile tam zamanında hata ayıklama Visual Studio:

- Windows Hata Bildirimi bilgisayarınızda hata işlemeyi ele alıyor olabilir.

  Bu sorunu düzeltmek için Kayıt Defteri Düzenleyicisi'ni kullanarak,  aşağıdaki kayıt defteri anahtarlarında **1** Değer verileri olan Devre Dışı **DWORD** Değeri ekleyin:

  - **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows Error Reporting**
  
  - (32 bit makineler için) **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  Daha fazla bilgi için [bkz. . WER ayarları.](/windows/desktop/wer/wer-settings)

- Bilinen Windows bir sorun, Tam Zamanında hata ayıklayıcısının başarısız olmasına neden olabilir.

  Düzeltme, aşağıdaki kayıt defteri anahtarlara Değer  **verileri** **1** olan bir **Otomatik DWORD** Değeri eklemektir:

  - **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (32 bit makineler için) **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

Tam Zamanında hata ayıklama sırasında aşağıdaki hata iletilerini alabilirsiniz:

- **Kilitlenme sürecine eklenemiyor. Belirtilen program bir Windows veya MS-DOS programı değildir.**

    Hata ayıklayıcısı başka bir kullanıcı altında çalışan bir işleme eklemeye çalıştı.

    Bu sorunu çözmek için Visual Studio'de İşleme Ekle'ye  >   tıklayın (veya **Ctrl** Alt P tuşlarına basın) ve Kullanılabilir İşlemler listesinde hata  +    +   **ayıklamak istediğiniz işlemi** bulun. sürecin adını bilmiyorsanız, Tam Zamanında Hata Ayıklayıcı iletişim **Visual Studio İşlem Kimliğini** bulun. Kullanılabilir İşlemler listesinde **işlemi seçin ve** Ekle'yi **seçin.** Tam **Zamanında** hata ayıklayıcısı iletişim kutusunu açmak için Hayır'ı seçin.

- **Hiçbir kullanıcı oturum açmadı olduğundan hata ayıklayıcı başlatılamadı.**

    Konsolda oturum açmış bir kullanıcı yoktur, bu nedenle Tam Zamanında hata ayıklama iletişim kutusunu görüntülemek için bir kullanıcı oturumu yoktur.

    Bu sorunu çözmek için makinede oturum açma.

- **Sınıf kayıtlı değil.**

    Hata ayıklayıcısı büyük olasılıkla bir yükleme sorunu nedeniyle kayıtlı değil bir COM sınıfı oluşturma denemesi yaptı.

    Bu sorunu düzeltmek için, Visual Studio Yükleyicisi yüklemenizi yeniden yüklemek veya onarmak Visual Studio kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Seçenekler, Hata Ayıklama, Tam Zamanında iletişim kutusu](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu bir işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz bu işleme ekleme](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
