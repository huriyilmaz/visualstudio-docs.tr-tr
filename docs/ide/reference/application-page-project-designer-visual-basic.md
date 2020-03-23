---
title: VB proje özelliklerinin uygulama sayfası
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe303f86b282e7e803dacc1dd8f4d3c1d6b72121
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595819"
---
# <a name="application-page-project-designer-visual-basic"></a>Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)

Projenin uygulama ayarlarını ve özelliklerini belirtmek için Proje Tasarımcısı'nın **Uygulama** sayfasını kullanın.

**Uygulama** sayfasına erişmek için **Çözüm Gezgini'nde**bir proje düğümü **(Çözüm** düğümü değil) seçin. Ardından menü çubuğunda **Project** > **Properties'i** seçin. Proje **Tasarımcısı** göründüğünde, **Uygulama** sekmesini seçin.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Genel uygulama ayarları

Aşağıdaki seçenekler, bir uygulama için genel ayarları yapılandırmanızı sağlar.

### <a name="assembly-name"></a>Montaj adı

Derleme bildirimini içerecek çıktı dosyasının adını belirtir. Bu özelliği değiştirirseniz, **Çıktı Adı** özelliği de değişir.

/out [(Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out) derleyici anahtarını kullanarak bir komut isteminden çıktı dosyasının adını da belirtebilirsiniz.

Bu özelliğe programlı olarak nasıl erişilisi hakkında bilgi için bkz. <xref:VSLangProj.ProjectProperties.AssemblyName%2A>

### <a name="root-namespace"></a>Kök ad alanı

Projedeki tüm dosyalar için temel ad alanını belirtir. Örneğin, **Root Namespace'i** ayarlarsanız `Project1` ve `Class1` kodunuzdaki herhangi bir ad alanının `Project1.Class1`dışında varsa, ad alanı . Kodda bir `Class2` ad alanınız `Order` varsa, ad alanı `Project1.Order.Class2`.

Kök Ad **Alanı'nı**temizlerseniz, projenizin ad alanı yapısını kodolarak belirtebilirsiniz.

> [!NOTE]
> `Global` Ad Alanı [Bildirimi'nde](/dotnet/visual-basic/language-reference/statements/namespace-statement)anahtar sözcüğü kullanırsanız, projenizin kök ad alanından bir ad alanı tanımlayabilirsiniz. **Root Namespace'i**temizlerseniz, `Global` bir `Global` `Namespace` deyimdeki anahtar kelime gereksinimini ortadan kaldıran üst düzey ad alanı olur. Daha fazla bilgi için [Visual Basic'teki Ad Alanlarında](/dotnet/visual-basic/programming-guide/program-structure/namespaces)"Ad Alanı İfadelerinde Genel Anahtar Kelime" başlıklı ana bakın.

Kodunuzda ad alanları oluşturma hakkında bilgi için [Bkz. Ad Alanı Bildirimi.](/dotnet/visual-basic/language-reference/statements/namespace-statement)

Kök ad alanı özelliği hakkında daha fazla bilgi için [bkz.](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace)

Bu özelliğe programlı olarak nasıl erişilisi hakkında bilgi için bkz. <xref:VSLangProj.ProjectProperties.RootNamespace%2A>

### <a name="target-framework-all-configurations"></a>Hedef çerçeve (tüm yapılandırmalar)

.NET sürümünü belirtir ve uygulama nın hedeflediğini belirtir. Bu seçenek, .NET'in bilgisayarınızda hangi sürümlerinin yüklendiğine bağlı olarak farklı değerlere sahip olabilir.

.NET Framework projeleri için varsayılan değer, projeyi oluşturduğunuzda belirttiğiniz hedef çerçeveyle eşleşir.

> [!NOTE]
> [Önkoşul İletişim Kutusu'nda](../../ide/reference/prerequisites-dialog-box.md) listelenen ön koşul paketleri, iletişim kutusunu ilk kez açtığınızda otomatik olarak ayarlanır. Daha sonra projenin hedef çerçevesini değiştirirseniz, yeni hedef çerçeveyle eşleşecek ön koşulları el ile belirtmeniz gerekir.

Daha fazla bilgi için çerçeve [hedefleme genel bakış'a](../../ide/visual-studio-multi-targeting-overview.md)bakın.

### <a name="application-type"></a>Uygulama türü

Oluşturmak için uygulama türünü belirtir. Değerler proje türüne bağlı olarak farklıdır. Örneğin, bir **Windows Forms App** projesi için **Windows Forms Uygulaması,** **Sınıf Kitaplığı,** **Konsol Uygulaması,** **Windows Hizmeti**veya Web **Denetim Kitaplığı**belirtebilirsiniz.

Bir web uygulama projesi için **Sınıf Kitaplığı**belirtmeniz gerekir.

**Uygulama türü** özelliği hakkında daha fazla bilgi için [bkz.](/dotnet/visual-basic/reference/command-line-compiler/target) Bu özelliğe programlı olarak nasıl erişilisin gerektiği hakkında bilgi için bkz. <xref:VSLangProj.ProjectProperties.OutputType%2A>

### <a name="auto-generate-binding-redirects"></a>Otomatik oluşturma bağlama yönlendirmeleri

Uygulamanız veya bileşenleri aynı derlemenin birden fazla sürümüne başvuruyorsa, bağlama yönlendirmeleri projenize eklenir. Proje dosyasındaki bağlama yönlendirmelerini el ile tanımlamak istiyorsanız, **Otomatik oluşturma bağlama yönlendirmelerini**seçin.

Yeniden yönlendirme hakkında daha fazla bilgi için [bkz.](/dotnet/framework/configure-apps/redirect-assembly-versions)

### <a name="startup-form--startup-object--startup-uri"></a>Başlangıç formu / Başlangıç nesnesi / Başlangıç URI

Uygulamanın başlangıç formunu veya giriş noktasını belirtir.

**Uygulama çerçevesini etkinleştir** (varsayılan) seçilirse, bu liste Başlangıç **formu** olarak adlanır ve yalnızca uygulama çerçevesi nesneleri değil yalnızca başlangıç formlarını desteklediği için formları gösterir.

Proje bir WPF Tarayıcı Uygulaması ise, bu liste **Başlangıç URI**başlıklı ve varsayılan **Page1.xaml**olduğunu. **Başlangıç URI** listesi, uygulama başladığında uygulamanın görüntülediğiniz kullanıcı arabirimi kaynağını (XAML öğesi) belirtmenizi sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Application.StartupUri%2A>.

**Uygulama çerçevesini etkinleştir** temizlenirse, bu liste Başlangıç **nesnesi** `Sub Main`olur ve hem formları hem de sınıfları veya modülleri bir .

**Başlangıç nesnesi,** uygulama yüklendiğinde çağrılacak giriş noktasını tanımlar. Genellikle bu, uygulamanızdaki ana form veya uygulama `Sub Main` başladığında çalışması gereken yordam için ayarlanır. Sınıf kitaplıklarında bir giriş noktası olmadığından, bu özellik için tek seçenekleri **(Yok)**'dir. Daha fazla bilgi için bkz: [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Bu özelliğe programlı olarak <xref:VSLangProj.ProjectProperties.StartupObject%2A>erişmek için bkz.

### <a name="icon"></a>Simge

Program simgeniz olarak kullanmak istediğiniz .ico dosyasını ayarlar. Varolan bir grafiğe göz atmak için ** \<Gözat...>'yi** seçin. Daha fazla bilgi için [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (veya [/win32icon (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)numaralı kullanıcıya bakın. Bu özelliğe programlı olarak <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>erişmek için bkz.

### <a name="assembly-information"></a>Montaj Bilgileri

Derleme Bilgileri İletişim [Kutusu'nu](../../ide/reference/assembly-information-dialog-box.md)görüntülemek için bu düğmeyi tıklatın.

### <a name="enable-application-framework"></a>Uygulama çerçevesini etkinleştirme

Projenin uygulama çerçevesini kullanıp kullanmayacağı belirtilir. Bu seçeneğin ayarı Başlangıç **formu**/**Başlangıç nesnesinde**bulunan seçenekleri etkiler.

Bu onay kutusu seçilirse, uygulamanız standardı `Sub Main`kullanır. Bu onay kutusunu **seçmek, Windows uygulama çerçevesi özellikleri** bölümündeki özellikleri etkinleştirir ve ayrıca bir başlangıç formu seçmeniz için de gereklidir.

Bu onay kutusu temizlenirse, `Sub Main` uygulamanız **Başlangıç formunda**belirttiğiniz özelliği kullanır. Bu durumda, başlangıç nesnesi (yöntem `Sub Main` veya sınıfa özel) veya form belirtebilirsiniz. Ayrıca, **Windows uygulama çerçevesi özellikleri** bölümündeki seçenekler kullanılamaz hale gelir.

### <a name="view-windows-settings"></a>Windows Ayarlarını Görüntüle

*App.manifest* dosyasını oluşturmak ve açmak için bu düğmeyi tıklatın. Visual Studio uygulama için bildirim verileri oluşturmak için bu dosyayı kullanır. Ardından `<requestedExecutionLevel>` *app.manifest'teki* etiketi aşağıdaki gibi değiştirerek UAC'nin istediği yürütme düzeyini ayarlayın:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce bir düzey `asInvoker` veya sanallaştırılmış modda (hiçbir manifesto oluşturma) ile çalışır. Sanallaştırılmış modu belirtmek için, etiketin tamamını app.manifest'ten kaldırın.

Bildirim oluşturma hakkında daha fazla bilgi için [Windows Vista'da ClickOnce Dağıtım'a](../../deployment/clickonce-deployment-on-windows-vista.md)bakın.

## <a name="windows-application-framework-properties"></a>Windows uygulama çerçeve özellikleri

Aşağıdaki ayarlar **Windows uygulama çerçevesi özellikleri** bölümünde kullanılabilir. Bu seçenekler yalnızca **Uygulama çerçevesini etkinleştir** onay kutusu seçilirse kullanılabilir.

> [!TIP]
> Aşağıdaki bölümde Windows **uygulama çerçevesi özellikleri** Windows Presentation Foundation (WPF) uygulamalarına özgü ayarlar açıklanır.

### <a name="enable-xp-visual-styles"></a>XP görsel stillerini etkinleştirme

*Windows XP Temaları*olarak da bilinen Windows XP görsel stillerini etkinleştirir veya devre dışı kılabilir. Windows XP görsel stilleri, örneğin, yuvarlak köşeleri ve dinamik renklerle denetimler sağlar. Varsayılan etkindir.

### <a name="make-single-instance-application"></a>Tek örnek uygulaması yapma

Kullanıcıların uygulamanın birden çok örneğini çalıştırmasını önlemek için bu onay kutusunu seçin. Bu onay kutusu için varsayılan ayar *temizlenir,* bu da uygulamanın birden çok örneğinin çalıştırılmasına izin verir. Daha fazla bilgi <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> için olaya bakın.

### <a name="save-mysettings-on-shutdown"></a>Kapatmada My.Settings kaydet

Kullanıcılar bilgisayarlarını kapattıklarında uygulama `My.Settings` ayarlarının kaydedildiğinden belirtmek için bu onay kutusunu seçin. Varsayılan ayar etkinleştirildi. Bu seçenek devre dışı bırakılırsa, 'yi `My.Settings.Save`arayarak uygulama ayarlarını el ile kaydedebilirsiniz.

### <a name="authentication-mode"></a>Kimlik doğrulaması modu

Şu anda oturum açmış olan kullanıcıyı tanımlamak için Windows kimlik doğrulamasının kullanımını belirtmek için **Windows'u** (varsayılan) seçin. `My.User` Nesneyi kullanarak bu bilgileri çalışma zamanında alabilirsiniz. Varsayılan Windows kimlik doğrulama yöntemlerini kullanmak yerine kullanıcıların kimliğini doğrulamak için kendi kodunuzu sağlayacaksanız **Uygulama tanımlı'yı** seçin.

### <a name="shutdown-mode"></a>Kapatma modu

Diğer formlar açık olsa bile, başlangıç formu kapandığında başvuru nun ne zaman açık olduğunu belirtmek için **başlangıç formunun ne zaman kapandığını** (varsayılan) seçin. Select **When last form closes** to specify that the application exit when the last form is closed or when `My.Application.Exit` or the `End` statement is called explicitly.

Açıkça aradığınızda `Shutdown`uygulamanın çıktığını belirtmek için **Açık kapatmada'yı** seçin.

Son pencere kapandığında veya açıkça aradığınızda `Shutdown`uygulamanın çıktığını belirtmek için son **pencereyi kapatan Son Pencere'yi** seçin. Bu varsayılan ayardır.

Ana pencere kapandığında veya açıkça aradığınızda `Shutdown`uygulamanın çıktığını belirtmek için ana **pencereyi kapat'ı** seç' in ' i seçin.

### <a name="splash-screen"></a>Giriş ekranı

Sıçrama ekranı olarak kullanmak istediğiniz formu seçin. Daha önce bir form veya şablon kullanarak bir sıçrama ekranı oluşturmuş olmalısınız. Varsayılan **değer (Yok)** olur.

### <a name="view-application-events"></a>Uygulama Olaylarını Görüntüle

Uygulama çerçevesi `Startup`olayları , , , `Shutdown` `UnhandledException` `StartupNextInstance` ve `NetworkAvailabilityChanged`. Belirli uygulama çerçevesi yöntemlerini de geçersiz kılabilirsiniz. Örneğin, sıçrama ekranının ekran davranışını geçersiz kılarak `OnInitialize`değiştirebilirsiniz.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Windows Presentation Foundation (WPF) uygulamaları için Windows uygulama çerçevesi özellikleri

Proje bir Windows Sunu Temeli (WPF) uygulaması olduğunda, aşağıdaki ayarlar **Windows uygulama çerçevesi özellikleri** bölümünde kullanılabilir. Bu seçenekler yalnızca **Uygulama çerçevesini etkinleştir** onay kutusu seçilirse kullanılabilir. Bu tabloda listelenen seçenekler yalnızca WPF veya WPF tarayıcı uygulamaları için kullanılabilir. WPF Kullanıcı Denetimi veya Özel Denetim kitaplıkları için kullanılamazlar.

### <a name="shutdown-mode"></a>Kapatma modu

Bu özellik yalnızca Windows Presentation Foundation (WPF) uygulamaları için geçerlidir.

Açıkça aradığınızda <xref:System.Windows.Application.Shutdown%2A>uygulamanın çıktığını belirtmek için **Açık kapatmada'yı** seçin.

Son pencere kapandığında veya açıkça aradığınızda <xref:System.Windows.Application.Shutdown%2A>uygulamanın çıktığını belirtmek için son **pencereyi kapatan Son Pencere'yi** seçin. Bu varsayılan ayardır.

Ana pencere kapandığında veya açıkça aradığınızda <xref:System.Windows.Application.Shutdown%2A>uygulamanın çıktığını belirtmek için ana **pencereyi kapat'ı** seç' in ' i seçin.

Bu ayarı kullanma hakkında daha fazla bilgi için bkz.<xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>XAML'yi ede

Bu düğme XAML düzenleyicisinde uygulama tanım dosyasını (Application.xaml) açar. Bu düğmeyi tıklattığınızda *Application.xaml* uygulama tanımı düğümünde açılır. Kaynakları tanımlamak gibi belirli görevleri gerçekleştirmek için bu dosyayı yeniden gerçekleştirmeniz gerekebilir. Uygulama tanım dosyası yoksa, Proje Tasarımcısı bir dosya oluşturur.

### <a name="view-application-events"></a>Uygulama Olaylarını Görüntüle

Bu düğme `Application` bir kod düzenleyicisinde sınıf dosyasını *(Application.xaml.vb)* açar. Dosya yoksa, Proje Tasarımcısı uygun sınıf adı ve ad alanına sahip bir dosya oluşturur.

Nesne, <xref:System.Windows.Application> belirli uygulama durumu değişiklikleri gerçekleştiğinde (örneğin, uygulama başlatma veya kapatmada) olayları yükseltir. Bu sınıfın ortaya çıkardığı olayların tam listesi <xref:System.Windows.Application>için bkz. Bu olaylar `Application` kısmi sınıfın kullanıcı kodu bölümünde işlenir.
