---
title: VB proje özelliklerinin uygulama sayfası
description: Projenin uygulama ayarlarını ve özelliklerini belirtmek için Visual Basic Project Tasarımcısı'nın Uygulama sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6df9268a66e34e0b523356e118c444a94e4c73933fff7643da03df9c268f2ef0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121232685"
---
# <a name="application-page-project-designer-visual-basic"></a>Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)

Projenin **uygulama** ayarlarını ve özelliklerini Project Tasarımcısı'nın Uygulama sayfasını kullanın.

Uygulama sayfasına **erişmek için,** uygulamasında bir proje düğümü **(Çözüm düğümü** değil) **Çözüm Gezgini.** Ardından menü **Project**  >  **Özellikler'i** seçin. Project **Tasarımcısı** görüntülendiğinde Uygulama **sekmesini** seçin.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Genel uygulama ayarları

Aşağıdaki seçenekler, bir uygulamanın genel ayarlarını yapılandırmaya olanak sağlar.

### <a name="assembly-name"></a>Derleme adı

Derleme bildirimini içeren çıkış dosyasının adını belirtir. Bu özelliği değiştirirsanız Çıkış **Adı özelliği** de değişir.

/out [(Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out) derleyici anahtarını kullanarak komut isteminden çıkış dosyasının adını da belirtebilirsiniz.

Bu özelle program aracılığıyla nasıl erişilen hakkında bilgi için bkz. <xref:VSLangProj.ProjectProperties.AssemblyName%2A> .

### <a name="root-namespace"></a>Kök ad alanı

Proje içinde tüm dosyalar için temel ad alanını belirtir. Örneğin, Kök Ad Alanı'nın **olarak ayarlanırsa** ve kodunda herhangi bir ad alanının dışında bir ad alanı `Project1` `Class1` varsa, ad alanı `Project1.Class1` olur. Kod içinde bir `Class2` ad alanı `Order` varsa, ad alanı `Project1.Order.Class2` olur.

Kök Ad Alanını **temizlersanız,** projenizin ad alanı yapısını kodda belirtebilirsiniz.

> [!NOTE]
> Bir Namespace `Global` Deyiminde anahtar [sözcüğünü kullanırsanız,](/dotnet/visual-basic/language-reference/statements/namespace-statement)projenizin kök ad alanının dışında bir ad alanı tanımlayabilirsiniz. Kök Ad Alanını **temizlersanız,** bir deyiminde anahtar sözcüğüne olan ihtiyacı ortadan `Global` kaldıran üst `Global` düzey ad alanı `Namespace` olur. Daha fazla bilgi için, Visual Basic'daki Ad Alanları'nın ["Ad Alanı Deyimleri'ne Genel Anahtar Visual Basic.](/dotnet/visual-basic/programming-guide/program-structure/namespaces)

Kodunda ad alanları oluşturma hakkında bilgi için bkz. [Namespace Deyimi.](/dotnet/visual-basic/language-reference/statements/namespace-statement)

Kök ad alanı özelliği hakkında daha fazla bilgi için bkz. [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Bu özelle program aracılığıyla nasıl erişilen hakkında bilgi için bkz. <xref:VSLangProj.ProjectProperties.RootNamespace%2A> .

### <a name="target-framework-all-configurations"></a>Hedef çerçeve (tüm yapılandırmalar)

Uygulamanın hedeflemektedir .NET sürümünü belirtir. Bu seçenek, bilgisayarınızda yüklü olan .NET sürümlerine bağlı olarak farklı değerlere sahip olabilir.

Bu .NET Framework için varsayılan değer, projeyi oluşturulduğunda belirttiğiniz hedef çerçeveyle eşler.

> [!NOTE]
> Önkoşullar İletişim Kutusunda listelenen [önkoşul](../../ide/reference/prerequisites-dialog-box.md) paketleri, iletişim kutusunu ilk kez açsanız otomatik olarak ayarlanır. Projenin hedef çerçevesini daha sonra değiştirirsiniz, yeni hedef çerçeveyle eşleşmesi için önkoşulları el ile belirtmeniz gerekir.

Daha fazla bilgi için [bkz. Çerçeve hedeflemeye genel bakış.](../../ide/visual-studio-multi-targeting-overview.md)

### <a name="application-type"></a>Uygulama türü

Derlemek için uygulama türünü belirtir. Değerler, proje türüne bağlı olarak farklıdır. Örneğin, bir **Windows Forms Uygulaması** projesi için Windows Forms **Uygulaması,** **Sınıf Kitaplığı,** Konsol **Uygulaması**, **Windows Hizmeti** veya Web Denetim Kitaplığı **belirtebilirsiniz.**

Bir web uygulaması projesi için Sınıf Kitaplığını **belirtmeniz gerekir.**

Uygulama türü özelliği hakkında daha **fazla bilgi** için bkz. [/target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Bu özelle program aracılığıyla nasıl erişilen hakkında bilgi için bkz. <xref:VSLangProj.ProjectProperties.OutputType%2A> .

### <a name="auto-generate-binding-redirects"></a>Bağlama yeniden yönlendirmelerini otomatik oluşturma

Bağlama yeniden yönlendirmeleri, uygulama veya bileşenleri aynı derlemenin birden fazla sürümüne başvurursa projenize eklenir. Proje dosyasında bağlama yeniden yönlendirmelerini el ile tanımlamak için Bağlamayı otomatik oluştur yeniden **yönlendirmeleri'nin seçimini kaldırın.**

Yeniden yönlendirme hakkında daha fazla bilgi için [bkz. Derleme sürümlerini yeniden yönlendirme.](/dotnet/framework/configure-apps/redirect-assembly-versions)

### <a name="startup-form--startup-object--startup-uri"></a>Başlangıç formu / Başlangıç nesnesi / Başlangıç URI'si

Uygulamanın başlangıç formunu veya giriş noktasını belirtir.

Uygulama **çerçevesini etkinleştir** seçiliyse (varsayılan), bu  liste Başlangıç formu başlıklıdır ve uygulama çerçevesi nesneleri değil yalnızca başlangıç formlarını desteklediği için yalnızca formları gösterir.

Proje bir WPF Tarayıcı Uygulaması ise, bu liste Başlangıç **URI'sini ve** varsayılan değer **Page1.xaml'dir.** Başlangıç **URI'sı** listesi, uygulama başlatıldığında uygulamanın görüntüleyeni kullanıcı arabirimi kaynağını (XAML öğesi) belirtmenizi sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Application.StartupUri%2A>.

Uygulama **çerçevesini etkinleştir** temizli ise, bu liste **Başlangıç** nesnesi olur ve hem formları hem de sınıfları veya modüllerini bir ile `Sub Main` gösterir.

**Başlangıç nesnesi,** uygulama yüklenirken çağrıl olacak giriş noktasını tanımlar. Genellikle bu, uygulamanın ana formuna veya uygulama başlatıldığında `Sub Main` çalışması gereken yordama ayarlanır. Sınıf kitaplıklarının bir giriş noktası yoktur, çünkü bu özellik için tek seçenekleri **(Hiçbiri) 'dır.** Daha fazla bilgi için bkz. [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Bu özelle program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.StartupObject%2A> .

### <a name="icon"></a>Simge

Program simgesi olarak kullanmak istediğiniz .ico dosyasını ayarlar. Mevcut **\<Browse...>** bir grafı bulmak için seçin. Daha fazla bilgi için bkz. [/win32icon (veya /win32icon (C# Derleyici Seçenekleri).](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) [](/dotnet/visual-basic/reference/command-line-compiler/win32icon) Bu özelle program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A> .

### <a name="assembly-information"></a>Derleme Bilgileri

Derleme Bilgileri İletişim Kutusunu görüntülemek [için bu düğmeye tıklayın.](../../ide/reference/assembly-information-dialog-box.md)

### <a name="enable-application-framework"></a>Uygulama çerçevesini etkinleştirme

Bir projenin uygulama çerçevesini kullanıp kullanmayacaklarını belirtir. Bu seçeneğin ayarı Başlangıç formu Başlangıç **nesnesinde bulunan** / **seçenekleri etkiler.**

Bu onay kutusu seçiliyse, uygulamanız standart `Sub Main` kullanır. Bu onay kutusunu seçmek, uygulama çerçevesi **Windows** bölümündeki özellikleri sağlar ve ayrıca bir başlangıç formu seçmenizi gerektirir.

Bu onay kutusu temizse, uygulamanız Başlangıç formunda `Sub Main` belirttiğiniz **özeli kullanır.** Bu durumda, bir başlangıç nesnesi (bir yöntemde veya `Sub Main` sınıfta özel) veya bir form belirtebilirsiniz. Ayrıca, uygulama çerçevesi **Windows bölümündeki seçenekler** kullanılamaz duruma gelir.

### <a name="view-windows-settings"></a>Görünüm Windows Ayarlar

*App.manifest* dosyasını oluşturmak ve açmak için bu düğmeye tıklayın. Visual Studio uygulama için bildirim verileri oluşturmak için bu dosyayı kullanır. Ardından app.manifest içinde etiketini aşağıdaki gibi değiştirerek UAC istenen `<requestedExecutionLevel>` *yürütme* düzeyini ayarlayın:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce düzeyiyle veya `asInvoker` sanallaştırılmış modda çalışır (bildirim oluşturma yoktur). Sanallaştırılmış modu belirtmek için app.manifest'den etiketin tamamını kaldırın.

Bildirim oluşturma hakkında daha fazla bilgi için [bkz. ClickOnce Vista'da Windows dağıtımı.](../../deployment/clickonce-deployment-on-windows-vista.md)

## <a name="windows-application-framework-properties"></a>Windows çerçevesi özelliklerini değiştirme

Aşağıdaki ayarlar uygulama çerçevesi **Windows bölümünde** kullanılabilir. Bu seçenekler yalnızca Uygulama çerçevesini **etkinleştir onay kutusu** seçiliyse kullanılabilir.

> [!TIP]
> Bunu takip eden bölümde, Windows (WPF) uygulamalarına özgü uygulama Windows Presentation Foundation özellikleri ayarları açıkmektedir. 

### <a name="enable-xp-visual-styles"></a>XP görsel stillerini etkinleştirme

Xp Temaları olarak Windows xp görsel stillerini etkinleştiren veya devre *Windows devre dışı bıraktır.* Windows XP görsel stilleri, örneğin, yuvarlak köşeler ve dinamik renklere sahip denetimleri etkinleştirir. Varsayılan değer etkindir.

### <a name="make-single-instance-application"></a>Tek örnekli uygulama yapma

Kullanıcıların uygulamanın birden çok örneğini çalıştırmasını önlemek için bu onay kutusunu seçin. Bu onay kutusunun varsayılan ayarı, *uygulamanın* birden çok örneğinin çalışmasına izin veren temizdir. Daha fazla bilgi için <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> bkz. olayı.

### <a name="save-mysettings-on-shutdown"></a>Kaydet: My. Ayarlar Kapatma sırasında

Kullanıcılar bilgisayarlarını kapattıklarında uygulama ayarlarının `My.Settings` kaydedilebilir olduğunu belirtmek için bu onay kutusunu işaretleyin. Varsayılan ayar etkindir. Bu seçenek devre dışı bırakılırsa, çağırarak uygulama ayarlarını el ile `My.Settings.Save` kaydedebilirsiniz.

### <a name="authentication-mode"></a>Kimlik doğrulaması modu

Oturum **Windows** kullanıcının kimliğini belirlemek için Windows (varsayılan) seçeneğini belirtin. bu bilgileri çalışma zamanında nesnesini kullanarak `My.User` edinebilirsiniz. Varsayılan **kimlik doğrulama yöntemlerini** kullanmak yerine kullanıcıların kimliğini doğrulamak için kendi kodunuzu sağlayacaksanız Uygulama tanımlı'Windows seçin.

### <a name="shutdown-mode"></a>Kapatma modu

Diğer **formlar açık olsa bile,** başlangıç formu kapanıyor olarak ayar olduğunda uygulamanın çıkış çıkar seçeneğini belirtmek için Başlangıç formu kapanıyor (varsayılan) öğesini seçin. Son **form kapanıyor seçeneğini belirterek** uygulamanın son form kapatılan veya deyiminin açıkça çağrıldı olduğu zaman çıkış `My.Application.Exit` olarak `End` belirtebilirsiniz.

Açıkça kapatıldığında uygulamanın çıkış yaptığınızda çıkış olduğunu belirtmek için **Açık Kapat '** ı seçin `Shutdown` .

Son pencere kapandığında veya açıkça çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **son pencere Kapat '** ı seçin `Shutdown` . Bu varsayılan ayardır.

Ana pencere kapandığında veya açıkça çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **ana pencerede Kapat '** ı seçin `Shutdown` .

### <a name="splash-screen"></a>Giriş ekranı

Giriş ekranı olarak kullanmak istediğiniz formu seçin. Daha önce bir form veya şablon kullanarak bir giriş ekranı oluşturmuş olmanız gerekir. Varsayılan değer **(yok)**.

### <a name="view-application-events"></a>Uygulama olaylarını görüntüle

Uygulama çerçevesi olayları,, ve için olay yazabileceğiniz bir olay kodu dosyası göstermek için bu düğmeye tıklayın `Startup` `Shutdown` `UnhandledException` `StartupNextInstance` `NetworkAvailabilityChanged` . Ayrıca, belirli uygulama çerçevesi yöntemlerini geçersiz kılabilirsiniz. Örneğin, giriş ekranının görüntüleme davranışını geçersiz kılarak değiştirebilirsiniz `OnInitialize` .

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Windows Presentation Foundation (WPF) uygulamaları için Windows uygulama çerçevesi özellikleri

bu ayarlar, proje bir Windows Presentation Foundation (WPF) uygulaması olduğunda **Windows uygulama çerçevesi özellikleri** bölümünde bulunur. Bu seçenekler yalnızca **uygulama çerçevesini etkinleştir** onay kutusu seçiliyse kullanılabilir. Bu tabloda listelenen seçenekler yalnızca WPF veya WPF tarayıcı uygulamaları için kullanılabilir. Bunlar WPF Kullanıcı denetimi veya özel denetim kitaplıkları için kullanılamaz.

### <a name="shutdown-mode"></a>Kapalı modu

bu özellik yalnızca Windows Presentation Foundation (WPF) uygulamaları için geçerlidir.

Açıkça kapatıldığında uygulamanın çıkış yaptığınızda çıkış olduğunu belirtmek için **Açık Kapat '** ı seçin <xref:System.Windows.Application.Shutdown%2A> .

Son pencere kapandığında veya açıkça çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **son pencere Kapat '** ı seçin <xref:System.Windows.Application.Shutdown%2A> . Bu varsayılan ayardır.

Ana pencere kapandığında veya açıkça çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **ana pencerede Kapat '** ı seçin <xref:System.Windows.Application.Shutdown%2A> .

Bu ayarı kullanma hakkında daha fazla bilgi için bkz. <xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>XAML düzenleme

Bu düğme, XAML düzenleyicisinde uygulama tanım dosyasını (Application. xaml) açar. Bu düğmeye tıkladığınızda, Application *. xaml* uygulama tanımı düğümünde açılır. Kaynakları tanımlama gibi belirli görevleri gerçekleştirmek için bu dosyayı düzenlemeniz gerekebilir. uygulama tanımı dosyası yoksa Project tasarımcısı bir tane oluşturur.

### <a name="view-application-events"></a>Uygulama olaylarını görüntüle

Bu düğme `Application` bir kod düzenleyicisinde sınıf dosyasını (*Application. xaml. vb*) açar. dosya yoksa Project tasarımcı, uygun sınıf adı ve ad alanıyla bir tane oluşturur.

<xref:System.Windows.Application>Nesne, belirli uygulama durumu değişiklikleri oluştuğunda (örneğin, uygulama başlangıcında veya kapatılırken) olaylar oluşturur. Bu sınıfın sunduğu olayların tam listesi için bkz <xref:System.Windows.Application> .. Bu olaylar, kısmi sınıfın Kullanıcı kodu bölümünde işlenir `Application` .
