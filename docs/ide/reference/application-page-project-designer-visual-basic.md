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
ms.openlocfilehash: 245bb2642a73e1b995841dd06a821a7e9b127020
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094288"
---
# <a name="application-page-project-designer-visual-basic"></a>Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)

Projenin **uygulama** ayarlarını ve özelliklerini Project Tasarımcısı'nın Uygulama sayfasını kullanın.

Uygulama sayfasına **erişmek için,** uygulamasında bir proje düğümü **(Çözüm düğümü** değil) **Çözüm Gezgini.** Ardından **menü Project**  >  **Özellikler'i** seçin. Project **Tasarımcısı** görüntülendiğinde Uygulama **sekmesini** seçin.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Genel uygulama ayarları

Aşağıdaki seçenekler, bir uygulamanın genel ayarlarını yapılandırmaya olanak sağlar.

### <a name="assembly-name"></a>Derleme adı

Derleme bildirimini içeren çıkış dosyasının adını belirtir. Bu özelliği değiştirirsanız Çıkış **Adı özelliği** de değişir.

/out [(Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out) derleyici anahtarını kullanarak komut isteminden çıkış dosyasının adını da belirtebilirsiniz.

Bu özelle program aracılığıyla nasıl erişilen hakkında bilgi için bkz. <xref:VSLangProj.ProjectProperties.AssemblyName%2A> .

### <a name="root-namespace"></a>Kök ad alanı

Proje içinde tüm dosyalar için temel ad alanını belirtir. Örneğin, Kök Ad Alanı'nın **olarak ayarlanırsa** ve kodunda herhangi bir ad alanının dışında bir ad `Project1` alanı `Class1` varsa, ad alanı `Project1.Class1` olur. Kod içinde bir `Class2` ad `Order` alanınız varsa, ad alanı `Project1.Order.Class2` olur.

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

Derlemek için uygulama türünü belirtir. Değerler, proje türüne bağlı olarak farklıdır. Örneğin, bir **Windows Forms Uygulaması** projesi için Windows Forms **Uygulaması,** **Sınıf** **Kitaplığı,** Konsol Uygulaması , **Windows Hizmeti** veya Web Denetim Kitaplığı **belirtebilirsiniz.**

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

**Başlangıç nesnesi,** uygulama yüklenirken çağrıl olacak giriş noktasını tanımlar. Genellikle bu, uygulamanın ana formuna veya uygulama başlatıldığında `Sub Main` çalışması gereken yordama ayarlanır. Sınıf kitaplıklarının bir giriş noktası yoktur, çünkü bu özellik için tek seçenekleri **(Hiçbiri) 'tir.** Daha fazla bilgi için bkz. [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Bu özelle program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.StartupObject%2A> .

### <a name="icon"></a>Simge

Program simgesi olarak kullanmak istediğiniz .ico dosyasını ayarlar. Mevcut **\<Browse...>** bir grafı bulmak için seçin. Daha fazla bilgi için bkz. [/win32icon (veya /win32icon (C# Derleyici Seçenekleri).](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) [](/dotnet/visual-basic/reference/command-line-compiler/win32icon) Bu özelle program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A> .

### <a name="assembly-information"></a>Derleme Bilgileri

Derleme Bilgileri İletişim Kutusunu görüntülemek [için bu düğmeye tıklayın.](../../ide/reference/assembly-information-dialog-box.md)

### <a name="enable-application-framework"></a>Uygulama çerçevesini etkinleştirme

Bir projenin uygulama çerçevesini kullanıp kullanmayacaklarını belirtir. Bu seçeneğin ayarı Başlangıç formu Başlangıç **nesnesinde bulunan** / **seçenekleri etkiler.**

Bu onay kutusu seçiliyse, uygulamanız standart `Sub Main` kullanır. Bu onay kutusunu seçmek, Windows **framework özellikleri** bölümündeki özellikleri sağlar ve bir başlangıç formu seçmenizi gerektirir.

Bu onay kutusu temizse, uygulamanız Başlangıç formunda `Sub Main` belirttiğiniz **özeli kullanır.** Bu durumda, bir başlangıç nesnesi (bir yöntemde veya `Sub Main` sınıfta özel) veya bir form belirtebilirsiniz. Ayrıca, uygulama çerçevesi **Windows bölümündeki seçenekler** kullanılamaz duruma gelir.

### <a name="view-windows-settings"></a>Görünüm Windows Ayarlar

*App.manifest* dosyasını oluşturmak ve açmak için bu düğmeye tıklayın. Visual Studio uygulama için bildirim verileri oluşturmak için bu dosyayı kullanır. Ardından app.manifest içinde etiketini aşağıdaki gibi değiştirerek UAC `<requestedExecutionLevel>` *istenen yürütme düzeyini* ayarlayın:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce düzeyiyle veya `asInvoker` sanallaştırılmış modda çalışır (bildirim oluşturma yoktur). Sanallaştırılmış modu belirtmek için app.manifest'den etiketin tamamını kaldırın.

Bildirim oluşturma hakkında daha fazla bilgi için [bkz. ClickOnce Vista'da Windows dağıtımı.](../../deployment/clickonce-deployment-on-windows-vista.md)

## <a name="windows-application-framework-properties"></a>Windows çerçevesi özelliklerini ayarlama

Aşağıdaki ayarlar uygulama çerçevesi **Windows bölümünde** kullanılabilir. Bu seçenekler yalnızca Uygulama çerçevesini **etkinleştir onay kutusu** seçiliyse kullanılabilir.

> [!TIP]
> Aşağıdaki bölümde, Windows (WPF) **uygulamalarına** özgü uygulama çerçevesi Windows Presentation Foundation ayarları açıkmektedir.

### <a name="enable-xp-visual-styles"></a>XP görsel stillerini etkinleştirme

XP Temaları olarak da Windows XP görsel stillerini etkinleştiren *Windows devre dışı bıraktır.* Windows XP görsel stilleri, örneğin, yuvarlak köşeler ve dinamik renklere sahip denetimleri etkinleştirir. Varsayılan değer etkindir.

### <a name="make-single-instance-application"></a>Tek örnekli uygulama yapma

Kullanıcıların uygulamanın birden çok örneğini çalıştırmasını önlemek için bu onay kutusunu seçin. Bu onay kutusunun varsayılan ayarı, *uygulamanın* birden çok örneğinin çalışmasına izin veren temizdir. Daha fazla bilgi için <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> bkz. olayı.

### <a name="save-mysettings-on-shutdown"></a>Kaydet: My. Ayarlar Kapatma sırasında

Kullanıcılar bilgisayarlarını kapattıklarında uygulama ayarlarının `My.Settings` kaydedilebilir olduğunu belirtmek için bu onay kutusunu işaretleyin. Varsayılan ayar etkindir. Bu seçenek devre dışı bırakılırsa, çağırarak uygulama ayarlarını el ile `My.Settings.Save` kaydedebilirsiniz.

### <a name="authentication-mode"></a>Kimlik doğrulaması modu

Oturum **Windows** kullanıcının kimliğini belirlemek üzere Windows (varsayılan) seçeneğini belirtin. bu bilgileri çalışma zamanında nesnesini kullanarak `My.User` edinebilirsiniz. Varsayılan **kimlik doğrulama yöntemlerini** kullanmak yerine kullanıcıların kimliğini doğrulamak için kendi kodunuzu sağlayacaksanız Uygulama tanımlı'Windows seçin.

### <a name="shutdown-mode"></a>Kapatma modu

Diğer **formlar açık olsa bile,** başlangıç formu kapanıyor olarak ayar olduğunda uygulamanın çıkış çıkar seçeneğini belirtmek için Başlangıç formu kapanıyor (varsayılan) öğesini seçin. Son **form kapanıyor seçeneğini belirterek** son form kapatılan veya deyiminin açıkça çağrılması için uygulamanın ne zaman `My.Application.Exit` `End` kapatılıyor olduğunu belirtin.

Açıkça **çağırarak uygulamanın** çıkış olarak çıkış yapmak için Açık kapatmada'ya `Shutdown` tıklayın.

Uygulamanın **son pencere kapanarak** veya açıkça çağırarak çıkışını belirtmek için Son pencere kapatılıyor'ı `Shutdown` seçin. Bu varsayılan ayardır.

Ana **pencere kapat'ı** seçerek ana pencere kapanıyor veya açıkça çağırarak uygulamanın çıkışını `Shutdown` belirtin.

### <a name="splash-screen"></a>Giriş ekranı

Giriş ekranı olarak kullanmak istediğiniz formu seçin. Daha önce bir form veya şablon kullanarak giriş ekranı oluşturdunız. Varsayılan değer **(Yok) değeridir.**

### <a name="view-application-events"></a>Uygulama Olaylarını Görüntüleme

Uygulama çerçevesi olayları , , ve için olayları yazarak bir olay kodu dosyası görüntülemek için `Startup` `Shutdown` bu düğmeye `UnhandledException` `StartupNextInstance` `NetworkAvailabilityChanged` tıklayın. Ayrıca belirli uygulama çerçevesi yöntemlerini geçersiz kılabilirsiniz. Örneğin, giriş ekranındaki görüntüleme davranışını geçersiz karak `OnInitialize` değiştirebilirsiniz.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Windows (WPF) uygulamaları Windows Presentation Foundation uygulama çerçevesi özelliklerini kullanma

Proje bir Windows Presentation Foundation (WPF) uygulaması olduğunda, Windows çerçevesi özellikleri bölümünde aşağıdaki ayarlar kullanılabilir.  Bu seçenekler yalnızca Uygulama çerçevesini **etkinleştir onay kutusu** seçiliyse kullanılabilir. Bu tabloda listelenen seçenekler yalnızca WPF veya WPF tarayıcı uygulamaları için kullanılabilir. WPF Kullanıcı Denetimi veya Özel Denetim kitaplıkları için kullanılamaz.

### <a name="shutdown-mode"></a>Kapatma modu

Bu özellik yalnızca Windows Presentation Foundation (WPF) uygulamaları için geçerlidir.

Açıkça **çağırarak uygulamanın** çıkış olarak çıkış yapmak için Açık kapatmada'ya <xref:System.Windows.Application.Shutdown%2A> tıklayın.

Uygulamanın **son pencere kapanarak** veya açıkça çağırarak çıkışını belirtmek için Son pencere kapatılıyor'ı <xref:System.Windows.Application.Shutdown%2A> seçin. Bu varsayılan ayardır.

Ana **pencere kapat'ı** seçerek ana pencere kapanıyor veya açıkça çağırarak uygulamanın çıkışını <xref:System.Windows.Application.Shutdown%2A> belirtin.

Bu ayarı kullanma hakkında daha fazla bilgi için bkz. <xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>XAML'yi düzenleme

Bu düğme, XAML düzenleyicisinde uygulama tanım dosyasını (Application.xaml) açar. Bu düğmeye tıklarken uygulama *tanımı düğümünde Application.xaml* açılır. Kaynak tanımlama gibi belirli görevleri gerçekleştirmek için bu dosyayı düzenlemeniz gerekir. Uygulama tanımı dosyası yoksa, Project Designer oluşturur.

### <a name="view-application-events"></a>Uygulama Olaylarını Görüntüleme

Bu düğme sınıf `Application` dosyasını (*Application.xaml.vb*) bir kod düzenleyicisinde açar. Dosya yoksa, Project Designer uygun sınıf adı ve ad alanı ile bir tane oluşturur.

Nesne, <xref:System.Windows.Application> belirli uygulama durumu değişiklikleri oluştuğunda (örneğin, uygulama başlatma veya kapatma sırasında) olayları başlatır. Bu sınıfın ortaya çıkar olduğu olayların tam listesi için bkz. <xref:System.Windows.Application> . Bu olaylar kısmi sınıfın kullanıcı kodu bölümünde `Application` ele.
