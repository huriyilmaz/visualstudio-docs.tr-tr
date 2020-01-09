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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595819"
---
# <a name="application-page-project-designer-visual-basic"></a>Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)

Projenin uygulama ayarlarını ve özelliklerini belirtmek için proje Tasarımcısı ' nın **uygulama** sayfasını kullanın.

**Uygulama** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü ( **çözüm** düğümünü değil) seçin. Ardından, menü çubuğunda **proje** > **Özellikler** ' i seçin. **Proje Tasarımcısı** göründüğünde **uygulama** sekmesini seçin.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Genel uygulama ayarları

Aşağıdaki seçenekler bir uygulama için genel ayarları yapılandırmanıza olanak tanır.

### <a name="assembly-name"></a>Bütünleştirilmiş kod adı

Derleme bildirimini içeren çıkış dosyasının adını belirtir. Bu özelliği değiştirirseniz, **Çıkış adı** özelliği de değişir.

Ayrıca, [/Out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out) derleyici anahtarını kullanarak bir komut isteminden çıkış dosyasının adını belirtebilirsiniz.

Bu özelliğe programlı bir şekilde erişme hakkında daha fazla bilgi için bkz. <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

### <a name="root-namespace"></a>Kök ad alanı

Projedeki tüm dosyalar için temel ad alanını belirtir. Örneğin, **kök ad alanını** `Project1` olarak ayarlarsanız ve kodunuzda herhangi bir ad alanı dışında bir `Class1` varsa, ad alanı `Project1.Class1`olur. Kodda `Order` bir ad alanında `Class2` varsa, ad alanı `Project1.Order.Class2`olur.

**Kök ad alanını**temizlerseniz, kodda projenizin ad alanı yapısını belirtebilirsiniz.

> [!NOTE]
> Bir [Namespace ifadesinde](/dotnet/visual-basic/language-reference/statements/namespace-statement)`Global` anahtar sözcüğünü kullanıyorsanız, projenizin kök ad alanından bir ad alanı tanımlayabilirsiniz. **Kök ad alanını**temizlerseniz `Global` en üst düzey ad alanı olur ve bu da `Namespace` deyimindeki `Global` anahtar kelimesinin gereksinimini ortadan kaldırır. Daha fazla bilgi için [Visual Basic ad alanları](/dotnet/visual-basic/programming-guide/program-structure/namespaces)Içindeki "ad alanı deyimlerine genel anahtar sözcük" başlığına bakın.

Kodunuzda ad alanlarını oluşturma hakkında daha fazla bilgi için bkz. [Namespace deyimleri](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Kök ad alanı özelliği hakkında daha fazla bilgi için bkz. [/RootNamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Bu özelliğe programlı bir şekilde erişme hakkında daha fazla bilgi için bkz. <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

### <a name="target-framework-all-configurations"></a>Hedef çerçeve (tüm yapılandırma)

Uygulamanın hedeflediği .NET sürümünü belirtir. Bu seçenek, bilgisayarınızda hangi .NET sürümlerinin yüklü olduğuna bağlı olarak farklı değerlere sahip olabilir.

.NET Framework projeleri için, varsayılan değer projeyi oluştururken belirttiğiniz hedef Framework ile eşleşir.

> [!NOTE]
> [Önkoşullar Iletişim kutusunda](../../ide/reference/prerequisites-dialog-box.md) listelenen önkoşul paketleri, iletişim kutusunu ilk kez açtığınızda otomatik olarak ayarlanır. Projenin hedef çerçevesini daha sonra değiştirirseniz, yeni hedef Framework 'ü eşleştirmek için önkoşulları el ile belirtmeniz gerekir.

Daha fazla bilgi için bkz. [Çerçeve hedefleme genel bakış](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Uygulama türü

Oluşturulacak uygulamanın türünü belirtir. Değerler proje türüne göre farklılık açmış. Örneğin, **Windows Forms bir uygulama** projesi Için **Windows Forms uygulama**, **sınıf kitaplığı**, **konsol uygulaması**, **Windows hizmeti**veya **Web denetim kitaplığı**belirtebilirsiniz.

Bir Web uygulaması projesi için **sınıf kitaplığı**belirtmeniz gerekir.

**Uygulama türü** özelliği hakkında daha fazla bilgi için bkz. [/target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Bu özelliğe programlı bir şekilde erişme hakkında daha fazla bilgi için bkz. <xref:VSLangProj.ProjectProperties.OutputType%2A>.

### <a name="auto-generate-binding-redirects"></a>Bağlama yeniden yönlendirmelerini otomatik oluştur

Uygulamanız veya bileşenleri aynı derlemenin birden fazla sürümüne başvurduğu takdirde bağlama yeniden yönlendirmeleri projenize eklenir. Proje dosyasında bağlama yeniden yönlendirmelerini el ile tanımlamak istiyorsanız **bağlama yeniden yönlendirmelerini otomatik oluştur**seçimini kaldırın.

Yeniden yönlendirme hakkında daha fazla bilgi için bkz. [derleme sürümlerini yeniden yönlendirme](/dotnet/framework/configure-apps/redirect-assembly-versions).

### <a name="startup-form--startup-object--startup-uri"></a>Başlangıç formu/başlangıç nesnesi/başlangıç URI 'SI

Uygulamanın başlangıç formunu veya giriş noktasını belirtir.

**Uygulama çerçevesini etkinleştir** seçilirse (varsayılan), bu liste **başlangıç formu** olarak belirlenir ve yalnızca form gösterir çünkü uygulama çerçevesi nesneleri değil yalnızca başlangıç formlarını destekler.

Proje bir WPF tarayıcı uygulamasıdır, bu liste **Başlangıç URI 'si**ve varsayılan olarak **Sayfa1. xaml**' dir. **Başlangıç URI** listesi, uygulama başladığında uygulamanın görüntülediği Kullanıcı arabirimi KAYNAĞıNı (XAML öğesi) belirtmenize olanak sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Application.StartupUri%2A>.

**Uygulama çerçevesini etkinleştir** ayarı silinirse, bu liste **Başlangıç nesnesi** haline gelir ve hem formları hem de sınıfları veya modülleri bir `Sub Main`gösterir.

**Başlangıç nesnesi** , uygulama yüklenirken çağrılacak giriş noktasını tanımlar. Genellikle bu, uygulamanızdaki ana forma veya uygulama başladığında çalışması gereken `Sub Main` yordama ayarlanır. Sınıf kitaplıklarının bir giriş noktası olmadığından, bu özellik için yalnızca seçeneği **(None)** olur. Daha fazla bilgi için bkz. [/Main](/dotnet/visual-basic/reference/command-line-compiler/main). Bu özelliğe program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

### <a name="icon"></a>Simge

Program simgenizin olarak kullanmak istediğiniz. ico dosyasını ayarlar. **\<gözatmaya seç...** var olan bir grafiğe gitmek için >. Daha fazla bilgi için bkz. [/Win32Icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (veya [/Win32ıcon (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)). Bu özelliğe program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

### <a name="assembly-information"></a>Derleme bilgileri

[Derleme bilgileri Iletişim kutusunu](../../ide/reference/assembly-information-dialog-box.md)göstermek için bu düğmeye tıklayın.

### <a name="enable-application-framework"></a>Uygulama çerçevesini etkinleştir

Projenin uygulama çerçevesini kullanıp kullanmayacağını belirtir. Bu seçeneğin ayarı, **Başlangıç formundaki**/**Başlangıç nesnesi**için kullanılabilir seçenekleri etkiler.

Bu onay kutusu işaretliyse, uygulamanız standart `Sub Main`kullanır. Bu onay kutusu seçildiğinde, **Windows uygulama çerçevesi özellikleri** bölümündeki Özellikler etkinleştirilir ve ayrıca bir başlangıç formu seçmeniz gerekir.

Bu onay kutusu silinirse, uygulamanız **Başlangıç formunda**belirttiğiniz özel `Sub Main` kullanır. Bu durumda, bir başlangıç nesnesi (bir yöntemde veya bir sınıfta özel `Sub Main`) ya da form belirtebilirsiniz. Ayrıca, **Windows Application Framework Özellikler** bölümündeki seçenekler kullanılamaz hale gelir.

### <a name="view-windows-settings"></a>Windows ayarlarını görüntüleme

*App. manifest* dosyasını oluşturmak ve açmak için bu düğmeye tıklayın. Visual Studio, uygulama için bildirim verileri oluşturmak üzere bu dosyayı kullanır. Ardından *app. manifest* 'teki `<requestedExecutionLevel>` etiketini aşağıdaki gıbı değiştirerek UAC istenen yürütme düzeyini ayarlayın:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce bir `asInvoker` düzeyi veya sanallaştırılmış modda (bildirim oluşturma olmadan) kullanılabilir. Sanallaştırılmış modu belirtmek için, tüm etiketi App. manifest öğesinden kaldırın.

Bildirim oluşturma hakkında daha fazla bilgi için bkz. [Windows Vista 'Da ClickOnce dağıtımı](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Windows uygulama çerçevesi özellikleri

**Windows uygulama çerçevesi özellikleri** bölümünde aşağıdaki ayarlar bulunur. Bu seçenekler yalnızca **uygulama çerçevesini etkinleştir** onay kutusu seçiliyse kullanılabilir.

> [!TIP]
> Bunu izleyen bölümde, Windows Presentation Foundation (WPF) uygulamalarına özgü **Windows uygulama çerçevesi özellikleri** ayarları açıklanmaktadır.

### <a name="enable-xp-visual-styles"></a>XP görsel stillerini etkinleştir

*WINDOWS XP temaları*olarak da BILINEN Windows XP görsel stillerini etkinleştirilir veya devre dışı bırakır. Windows XP görsel stilleri, yuvarlatılmış köşeler ve dinamik renklerle denetimleri sağlar. Varsayılan değer etkindir.

### <a name="make-single-instance-application"></a>Tek örnekli uygulama oluştur

Kullanıcıların uygulamanın birden çok örneğini çalıştırmasını engellemek için bu onay kutusunu işaretleyin. Bu onay kutusunun varsayılan ayarı *temizlenir*ve bu, uygulamanın birden çok örneğinin çalıştırılmasına izin verir. Daha fazla bilgi için <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> olayına bakın.

### <a name="save-mysettings-on-shutdown"></a>My. Settings 'i kapatmadan Kaydet

Kullanıcılar bilgisayarlarını kapatdıkları zaman uygulamanın `My.Settings` ayarlarının kaydedileceğini belirtmek için bu onay kutusunu işaretleyin. Varsayılan ayar etkindir. Bu seçenek devre dışıysa, `My.Settings.Save`çağırarak uygulama ayarlarını el ile kaydedebilirsiniz.

### <a name="authentication-mode"></a>Kimlik doğrulaması modu

Şu anda oturum açmış kullanıcıyı tanımlamak için Windows kimlik doğrulamasının kullanımını belirtmek üzere **Windows** (varsayılan) seçeneğini belirleyin. `My.User` nesnesini kullanarak, çalışma zamanında bu bilgileri alabilirsiniz. Varsayılan Windows kimlik doğrulama yöntemlerini kullanmak yerine, kullanıcıların kimliğini doğrulamak için kendi kodunuzu sağlayacağınızı **uygulama tanımlı** ' yı seçin.

### <a name="shutdown-mode"></a>Kapalı modu

Başlangıç formu kapandığında uygulamanın çıkış ' ı kapattığında, diğer formlar açık olsa bile, uygulamanın çıkış **biçimini seçin (** varsayılan). Son form kapatıldığında veya `My.Application.Exit` ya da `End` ifadesiyle açıkça çağrıldığında uygulamanın çıkış yapmak için **son form kapandığında** öğesini seçin.

`Shutdown`açıkça çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **Açık Kapat '** ı seçin.

Son pencere kapandığında veya `Shutdown`açık olarak çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **son pencere Kapat '** ı seçin. Varsayılan ayar budur.

Ana pencere kapandığında veya `Shutdown`açıkça çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **ana pencerede Kapat '** ı seçin.

### <a name="splash-screen"></a>Giriş ekranı

Giriş ekranı olarak kullanmak istediğiniz formu seçin. Daha önce bir form veya şablon kullanarak bir giriş ekranı oluşturmuş olmanız gerekir. Varsayılan değer **(yok)** .

### <a name="view-application-events"></a>Uygulama olaylarını görüntüle

`Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` ve `NetworkAvailabilityChanged`uygulama çerçevesi olayları için olay yazabileceğiniz bir olay kodu dosyası göstermek için bu düğmeye tıklayın. Ayrıca, belirli uygulama çerçevesi yöntemlerini geçersiz kılabilirsiniz. Örneğin, `OnInitialize`geçersiz kılarak giriş ekranının görüntüleme davranışını değiştirebilirsiniz.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Windows Presentation Foundation (WPF) uygulamaları için Windows uygulama çerçevesi özellikleri

Aşağıdaki ayarlar, proje bir Windows Presentation Foundation (WPF) uygulaması olduğunda **Windows uygulama çerçevesi özellikleri** bölümünde bulunur. Bu seçenekler yalnızca **uygulama çerçevesini etkinleştir** onay kutusu seçiliyse kullanılabilir. Bu tabloda listelenen seçenekler yalnızca WPF veya WPF tarayıcı uygulamaları için kullanılabilir. Bunlar WPF Kullanıcı denetimi veya özel denetim kitaplıkları için kullanılamaz.

### <a name="shutdown-mode"></a>Kapalı modu

Bu özellik yalnızca Windows Presentation Foundation (WPF) uygulamaları için geçerlidir.

<xref:System.Windows.Application.Shutdown%2A>açıkça çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **Açık Kapat '** ı seçin.

Son pencere kapandığında veya <xref:System.Windows.Application.Shutdown%2A>açık olarak çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **son pencere Kapat '** ı seçin. Varsayılan ayar budur.

Ana pencere kapandığında veya <xref:System.Windows.Application.Shutdown%2A>açıkça çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **ana pencerede Kapat '** ı seçin.

Bu ayarı kullanma hakkında daha fazla bilgi için bkz. <xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>XAML düzenleme

Bu düğme, XAML düzenleyicisinde uygulama tanım dosyasını (Application. xaml) açar. Bu düğmeye tıkladığınızda, Application *. xaml* uygulama tanımı düğümünde açılır. Kaynakları tanımlama gibi belirli görevleri gerçekleştirmek için bu dosyayı düzenlemeniz gerekebilir. Uygulama tanımı dosyası yoksa, proje Tasarımcısı bir tane oluşturur.

### <a name="view-application-events"></a>Uygulama olaylarını görüntüle

Bu düğme bir kod düzenleyicisinde `Application` sınıf dosyasını (*Application. xaml. vb*) açar. Dosya yoksa, proje Tasarımcısı uygun sınıf adı ve ad alanıyla bir tane oluşturur.

<xref:System.Windows.Application> nesnesi, bazı uygulama durumu değişiklikleri oluştuğunda (örneğin, uygulama başlangıcında veya kapatılırken) olaylar oluşturur. Bu sınıfın sunduğu olayların tam listesi için bkz. <xref:System.Windows.Application>. Bu olaylar `Application` kısmi sınıfının Kullanıcı kodu bölümünde işlenir.
