---
title: Tam Zamanında Hata Ayıklama
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad2814dffa75809a318dc7cebe7831b5ecec7d29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690603"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Visual Studio'da Tam Zamanında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio dışında çalışan bir uygulamada özel durum veya kilitlenme oluştuğunda, tam zamanında hata ayıklama Visual Studio 'Yu otomatik olarak başlatır. Bu, Visual Studio çalışmadığı zaman uygulamanızı test etmenizi ve bir sorun oluştuğunda Visual Studio ile hata ayıklamaya başlamanızı sağlar.

Tam zamanında hata ayıklama Windows Masaüstü uygulamaları için geçerlidir. Windows Evrensel uygulamaları için çalışmaz ve Görselleştiriciler gibi yerel bir uygulamada barındırılan yönetilen kod için çalışmaz.

## <a name="did-the-just-in-time-debugger-dialog-box-appear-when-trying-to-run-an-app"></a><a name="BKMK_Scenario"></a> Bir uygulamayı çalıştırmaya çalışırken tam zamanında hata ayıklayıcı iletişim kutusu görünüyor mu?

Visual Studio tam zamanında hata ayıklayıcı iletişim kutusunu gördüğünüzde yapmanız gereken işlemler, yapmaya çalıştığınız işlemlere bağlıdır:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>İletişim kutusundan kurtul etmek ve uygulamayı normal olarak çalıştırmak istiyorsanız

1. (Gelişmiş kullanıcılar) Visual Studio yüklüyse (veya daha önce yüklediyseniz ve kaldırdıysanız), [tam zamanında hata ayıklamayı devre dışı bırakın](#BKMK_Enabling) ve uygulamayı yeniden çalıştırmayı deneyin.

2. Internet Explorer 'da bir Web uygulaması çalıştırıyorsanız, betik hata ayıklamayı devre dışı bırakın.

    Internet Seçenekleri iletişim kutusunda betik hata ayıklamayı devre dışı bırakın. Bu **denetime denetim masası**  /  **ağı ve internet**  /  **Internet seçenekleri** 'nden erişebilirsiniz (tam adımlar Windows ve Internet Explorer sürümünüze bağlıdır).

    ![Jınternetoptions](../debugger/media/jitinternetoptions.png "Jınternetoptions")

3. Hatayı bulduğunuz Web sayfasını yeniden açın. Bu sorunu çözmezse, sorunu gidermek için Web uygulamasının sahibine başvurun.

4. Başka bir tür Windows uygulaması çalıştırıyorsanız, hatayı onarmak için uygulamanın sahibine başvurmanız ve sonra uygulamanın sabit sürümünü yeniden yüklemeniz gerekir.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Hatayı onarmak veya hata ayıklamak istiyorsanız (Gelişmiş kullanıcılar)

- Hatayla ilgili ayrıntılı bilgileri görüntülemek ve hata ayıklamayı denemek için [Visual Studio yüklü](https://visualstudio.microsoft.com/vs/older-downloads/) olmalıdır. Ayrıntılı yönergeler için bkz. [JIT kullanma](#BKMK_Using_JIT) . Hatayı çözemezse ve uygulamayı düzeltemedi, hatayı çözmek için uygulamanın sahibine başvurun.

## <a name="enable-or-disable-just-in-time-debugging"></a><a name="BKMK_Enabling"></a> Tam zamanında hata ayıklamayı etkinleştirme veya devre dışı bırakma
 Visual Studio **araçları/seçenekleri** Iletişim kutusundan tam zamanında hata ayıklamayı etkinleştirebilir veya devre dışı bırakabilirsiniz.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Tam zamanında hata ayıklamayı etkinleştirmek veya devre dışı bırakmak için

1. Visual Studio'yu açın. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. **Seçenekler** iletişim kutusunda, **hata ayıklama** klasörünü seçin.

3. **Hata ayıklama** klasöründe, **tam zamanında** sayfasını seçin.

4. **Şu kod türlerinde tam zamanında hata ayıklamayı etkinleştir** kutusunda, ilgili program türlerini seçin veya temizleyin: **yönetilen**, **Yerel**veya **betik**.

    Tam zamanında hata ayıklamayı devre dışı bırakmak için, etkinleştirildikten sonra, yönetici ayrıcalıklarıyla çalıştırıyor olmanız gerekir. Tam zamanında hata ayıklamayı etkinleştirmek bir kayıt defteri anahtarı ayarlar ve bu anahtarı değiştirmek için yönetici ayrıcalıkları gerekir.

5. **Tamam**’a tıklayın.

   Visual Studio artık bilgisayarınızda yüklü olmasa bile tam zamanında hata ayıklama hala etkinleştirilebilir. Visual Studio yüklü olmadığında, Visual Studio **Seçenekler** Iletişim kutusundan tam zamanında hata ayıklamayı devre dışı bırakayükleyemezsiniz. Bu durumda, Windows kayıt defterini düzenleyerek tam zamanında hata ayıklamayı devre dışı bırakabilirsiniz.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Kayıt defterini düzenleyerek tam zamanında hata ayıklamayı devre dışı bırakmak için

1. **Başlat** menüsünde, ara ve Çalıştır`regedit.exe`

2. Kayıt defteri **Düzenleyicisi** penceresinde, kayıt defteri girdilerini bulun ve silin:

    - HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework\DbgManagedDebugger

3. Bilgisayarınızda 64 bitlik bir işletim sistemi çalışıyorsa aşağıdaki kayıt defteri girdilerini de silin:

    - HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework\DbgManagedDebugger

4. Yanlışlıkla silmek veya diğer kayıt defteri anahtarlarını değiştirmek için dikkatli olmanız gerekmez.

5. **Kayıt defteri Düzenleyicisi** penceresini kapatın.

> [!NOTE]
> Sunucu tarafı bir uygulama için tam zamanında hata ayıklamayı devre dışı bırakmayı deniyorsanız ve bu adımlar sorunu gidermezse, IIS uygulama ayarlarında sunucu tarafı hata ayıklamayı kapatın ve yeniden deneyin.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Bir Windows formunda tam zamanında hata ayıklamayı etkinleştirmek için

1. Varsayılan olarak Windows Forms uygulamalar, kurtarabildiği takdirde programın çalışmaya devam etmesine izin veren bir üst düzey özel durum işleyicisine sahiptir. Örneğin, Windows Forms uygulamanız işlenmeyen bir özel durum oluşturursa, aşağıdaki gibi bir iletişim kutusu görürsünüz:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Windows Forms bir uygulamada tam zamanında hata ayıklamayı etkinleştirmek için aşağıdaki ek adımları gerçekleştirmeniz gerekir:

2. `jitDebugging` `true` `system.windows.form` machine.config veya.exe.config dosyasının bölümünde değerini olarak ayarlayın *\<application name>* :

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3. C++ Windows form uygulamasında, `DebuggableAttribute` bir. config dosyasında veya kodunuzda da ayarlamanız gerekir. [/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) ile ve [/OG](https://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435)olmadan derlerseniz, derleyici bu özniteliği sizin için ayarlar. Ancak, en iyi duruma getirilmeyen bir yayın derlemesinde hata ayıklamak istiyorsanız, bunu kendiniz ayarlamanız gerekir. Bunu, uygulamanızın AssemblyInfo. cpp dosyası olan aşağıdaki satırı ekleyerek yapabilirsiniz:

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Daha fazla bilgi için bkz. <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmk_using_jituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Tam zamanında hata ayıklamayı kullan
 Bu bölümde bir yürütülebilir dosya özel durum oluşturduğunda ne olacağı gösterilmektedir.

 Bu adımları izlemek için Visual Studio yüklü olmalıdır. Visual Studio yoksa, ücretsiz [Visual studio 2015 Community Edition](https://visualstudio.microsoft.com/vs/older-downloads/)'ı indirebilirsiniz.

 Visual Studio 'Yu yüklediğinizde, tam zamanında hata ayıklama varsayılan olarak etkinleştirilir.

 Bu bölümün amaçları doğrultusunda, Visual Studio 'da bir C# konsol uygulaması oluşturur <xref:System.NullReferenceException> .

 Visual Studio 'da, **ThrowsNullException**adlı bir C# konsol uygulaması (**dosya/yeni/proje/Visual C#/konsol uygulaması**) oluşturun. Visual Studio 'da proje oluşturma hakkında daha fazla bilgi için bkz. [Izlenecek yol: basit bir uygulama oluşturma](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Proje Visual Studio 'da açıldığında, Program.cs dosyasını açın. Main () yöntemini bir satırı konsola yazdıran aşağıdaki kodla değiştirin ve ardından bir NullReferenceException şunu oluşturur:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> Bu yordamın bir [sürüm yapılandırmasında](../debugger/how-to-set-debug-and-release-configurations.md)çalışması için [yalnızca kendi kodum](../debugger/just-my-code.md)kapatmanız gerekir. Visual Studio 'da **Araçlar/Seçenekler**' e tıklayın. **Seçenekler** Iletişim kutusunda **hata ayıklama**' yı seçin. **Enable yalnızca kendi kodum**denetimini kaldırın.

 Çözümü oluşturun (Visual Studio 'da, **Çözümü Derle/yeniden oluştur**' u seçin). Hata ayıklama veya sürüm yapılandırması seçeneklerinden birini belirleyebilirsiniz. Derleme konfigürasyonları hakkında daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).

 Yapı işlemi yürütülebilir bir ThrowsNullException.exe oluşturur. Bunu, C# projesini oluşturduğunuz klasörde bulabilirsiniz: **. ..\ThrowsNullException\ThrowsNullException\bin\Debug** veya **. ..\ThrowsNullException\ThrowsNullException\bin\Release**.

 ThrowsNullException.exe çift tıklayın. Şöyle bir komut penceresi görmeniz gerekir:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Birkaç saniye sonra bir hata penceresi görünür:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 **Iptal 'e**tıklamayın! Birkaç saniye sonra iki düğme görmeniz gerekir, **Hata Ayıkla** ve **Program Kapat**. **Hata Ayıkla**' ya tıklayın.

> [!CAUTION]
> Uygulamanız güvenilmeyen kod içeriyorsa, güvenlik uyarısı içeren bir iletişim kutusu görüntülenir. Bu iletişim kutusu, hata ayıklama ile devam edip etmemeye karar vermenize olanak sağlar. Hata ayıklamaya devam etmeden önce koda güvenip güvenmeyeceğinizi belirleyin. Kodu kendiniz yazdınız mı? Coder 'a güveniyor musunuz? Uygulama uzak bir makinede çalışıyorsa, işlemin adını tanıyor musunuz? Uygulama yerel olarak çalışıyor olsa bile, bu, güvenilir bir anlamına gelmez. Bilgisayarınızda çalışan kötü amaçlı kod olasılığını göz önünde bulundurun. Hata ayıklamak üzere olduğunuz kodun güvenilir olup olmadığına karar verirseniz **Hata Ayıkla**' ya tıklayın. Aksi takdirde, **Hata Ayıkla**' ya tıklayın.

 **Visual Studio tam zamanında hata ayıklayıcı** penceresi görünür:

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 **Olası hata ayıklayıcıları**altında, **Microsoft Visual Studio 2015 satırının yeni örneğinin** seçili olduğunu görmeniz gerekir. Henüz seçili değilse, şimdi seçin.

 Pencerenin en altında, **Seçili hata ayıklayıcıyı kullanarak hata ayıklamak**istiyor musunuz? altında **Evet**' e tıklayın.

 ThrowsNullException projesi Visual Studio 'nun yeni bir örneğinde açılarak yürütme, özel durumu oluşturan satırda durdurulur:

 ![Nullreferencesecondınstance](../debugger/media/nullreferencesecondinstance.png "Nullreferencesecondınstance")

 Bu noktada hata ayıklamayı başlatabilirsiniz. Bu gerçek bir uygulamatı ise kodun neden özel durumu yayımladığına ilişkin bilgi almanız gerekir.

## <a name="just-in-time-debugging-errors"></a>Tam zamanında hata ayıklama hataları
 program çöktüğünde iletişim kutusunu görmüyorsanız, bu durum bilgisayarınızdaki Windows Hata Bildirimi ayarlarından kaynaklanabilir. Daha fazla bilgi için bkz [.. WER ayarları](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 Tam zamanında hata ayıklama ile ilişkili aşağıdaki hata iletilerini görebilirsiniz.

- **Kilitlenen işleme iliştirilemiyor. Belirtilen program bir Windows veya MS-DOS programı değil.**

     Bu hata, başka bir kullanıcı olarak çalışan bir işleme iliştirmeye çalıştığınızda oluşur.

     Bu sorunu geçici olarak çözmek için, Visual Studio 'yu başlatın, **Hata Ayıkla** menüsünde **İşleme İliştir** Iletişim kutusunu açın ve **kullanılabilir işlemler** listesinde hata ayıklamak istediğiniz işlemi bulun. İşlemin adını bilmiyor değilseniz, **Visual Studio tam zamanında hata ayıklayıcı** iletişim kutusuna bakın ve işlem kimliğini not edin. **Kullanılabilir işlemler** listesinde işlemi seçin ve **Ekle**' ye tıklayın. **Visual Studio tam zamanında hata ayıklayıcı** Iletişim kutusunda **Hayır** ' a tıklayarak iletişim kutusunu kapatın.

- **Hiçbir Kullanıcı oturum açmamış olduğundan hata ayıklayıcı başlatılamadı.**

     Bu hata, Just-In-Time hata ayıklama işlemi, konsolda oturum açan kullanıcının olmadığı bir makinede Visual Studio 'Yu başlatmaya çalıştığında oluşur. Hiçbir Kullanıcı oturum açmamış olduğundan, tam zamanında hata ayıklama iletişim kutusunu göstermek için Kullanıcı oturumu yoktur.

     Bu sorunu gidermek için makinede oturum açın.

- **Sınıf kayıtlı değil.**

     Bu hata, hata ayıklayıcının, muhtemelen bir yükleme sorunu nedeniyle kayıtlı olmayan bir COM sınıfı oluşturmayı denediğini gösterir.

     Bu sorunu gidermek için kurulum disketini kullanarak Visual Studio yüklemenizi yeniden yükleyin veya onarın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Hata ayıklayıcı güvenlik](../debugger/debugger-security.md) [hata ayıklayıcı temelleri](../debugger/debugger-basics.md) [tam zamanında, hata ayıklama, Seçenekler iletişim kutusu](../debugger/just-in-time-debugging-options-dialog-box.md) [güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015) eklemeyin
