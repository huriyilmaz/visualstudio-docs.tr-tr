---
title: VB proje özelliklerinin uygulama sayfası
description: projenin uygulama ayarlarını ve özelliklerini belirtmek için Visual Basic Project tasarımcısının uygulama sayfasını nasıl kullanacağınızı öğrenin.
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

projenin uygulama ayarlarını ve özelliklerini belirtmek için Project tasarımcısının **uygulama** sayfasını kullanın.

**Uygulama** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü ( **çözüm** düğümünü değil) seçin. ardından   >  , menü çubuğunda Project **özellikler** ' i seçin. **Project tasarımcı** göründüğünde **uygulama** sekmesini seçin.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Genel uygulama ayarları

Aşağıdaki seçenekler bir uygulama için genel ayarları yapılandırmanıza olanak tanır.

### <a name="assembly-name"></a>Bütünleştirilmiş kod adı

Derleme bildirimini içeren çıkış dosyasının adını belirtir. Bu özelliği değiştirirseniz, **Çıkış adı** özelliği de değişir.

ayrıca, [/out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out) derleyici anahtarını kullanarak bir komut isteminden çıkış dosyasının adını belirtebilirsiniz.

Bu özelliğe programlı bir şekilde erişme hakkında daha fazla bilgi için bkz <xref:VSLangProj.ProjectProperties.AssemblyName%2A> ..

### <a name="root-namespace"></a>Kök ad alanı

Projedeki tüm dosyalar için temel ad alanını belirtir. Örneğin, **kök ad alanını** olarak ayarlarsanız `Project1` ve `Class1` kodunuzda herhangi bir ad alanı dışında bir alanınız varsa, ad alanı olur `Project1.Class1` . Kodda bir ad alanında varsa `Class2` `Order` , ad alanı olur `Project1.Order.Class2` .

**Kök ad alanını** temizlerseniz, kodda projenizin ad alanı yapısını belirtebilirsiniz.

> [!NOTE]
> `Global`Bir [Namespace ifadesinde](/dotnet/visual-basic/language-reference/statements/namespace-statement)anahtar sözcüğünü kullanıyorsanız, projenizin kök ad alanından bir ad alanı tanımlayabilirsiniz. **Kök ad alanını** temizlerseniz, `Global` üst düzey ad alanı haline gelir ve bu, `Global` bir deyimdeki anahtar kelimesinin gereksinimini ortadan kaldırır `Namespace` . Daha fazla bilgi için [Visual Basic ad alanları](/dotnet/visual-basic/programming-guide/program-structure/namespaces)Içindeki "ad alanı deyimlerine genel anahtar sözcük" başlığına bakın.

Kodunuzda ad alanlarını oluşturma hakkında daha fazla bilgi için bkz. [Namespace deyimleri](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Kök ad alanı özelliği hakkında daha fazla bilgi için bkz. [/RootNamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Bu özelliğe programlı bir şekilde erişme hakkında daha fazla bilgi için bkz <xref:VSLangProj.ProjectProperties.RootNamespace%2A> ..

### <a name="target-framework-all-configurations"></a>Hedef çerçeve (tüm yapılandırma)

Uygulamanın hedeflediği .NET sürümünü belirtir. Bu seçenek, bilgisayarınızda hangi .NET sürümlerinin yüklü olduğuna bağlı olarak farklı değerlere sahip olabilir.

.NET Framework projeleri için, varsayılan değer projeyi oluştururken belirttiğiniz hedef Framework ile eşleşir.

> [!NOTE]
> [Önkoşullar Iletişim kutusunda](../../ide/reference/prerequisites-dialog-box.md) listelenen önkoşul paketleri, iletişim kutusunu ilk kez açtığınızda otomatik olarak ayarlanır. Projenin hedef çerçevesini daha sonra değiştirirseniz, yeni hedef Framework 'ü eşleştirmek için önkoşulları el ile belirtmeniz gerekir.

Daha fazla bilgi için bkz. [Çerçeve hedefleme genel bakış](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Uygulama türü

Oluşturulacak uygulamanın türünü belirtir. Değerler proje türüne göre farklılık açmış. örneğin, **Windows Forms bir uygulama** projesi için **Windows Forms uygulama**, **sınıf kitaplığı**, **konsol uygulaması**, **Windows hizmeti** veya **Web denetim kitaplığı** belirtebilirsiniz.

Bir Web uygulaması projesi için **sınıf kitaplığı** belirtmeniz gerekir.

**Uygulama türü** özelliği hakkında daha fazla bilgi için bkz. [/target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Bu özelliğe programlı bir şekilde erişme hakkında daha fazla bilgi için bkz <xref:VSLangProj.ProjectProperties.OutputType%2A> ..

### <a name="auto-generate-binding-redirects"></a>Bağlama yeniden yönlendirmelerini otomatik oluştur

Uygulamanız veya bileşenleri aynı derlemenin birden fazla sürümüne başvurduğu takdirde bağlama yeniden yönlendirmeleri projenize eklenir. Proje dosyasında bağlama yeniden yönlendirmelerini el ile tanımlamak istiyorsanız **bağlama yeniden yönlendirmelerini otomatik oluştur** seçimini kaldırın.

Yeniden yönlendirme hakkında daha fazla bilgi için bkz. [derleme sürümlerini yeniden yönlendirme](/dotnet/framework/configure-apps/redirect-assembly-versions).

### <a name="startup-form--startup-object--startup-uri"></a>Başlangıç formu/başlangıç nesnesi/başlangıç URI 'SI

Uygulamanın başlangıç formunu veya giriş noktasını belirtir.

**Uygulama çerçevesini etkinleştir** seçilirse (varsayılan), bu liste **başlangıç formu** olarak belirlenir ve yalnızca form gösterir çünkü uygulama çerçevesi nesneleri değil yalnızca başlangıç formlarını destekler.

Proje bir WPF tarayıcı uygulamasıdır, bu liste **Başlangıç URI 'si** ve varsayılan olarak **Sayfa1. xaml**' dir. **Başlangıç URI** listesi, uygulama başladığında uygulamanın görüntülediği Kullanıcı arabirimi KAYNAĞıNı (XAML öğesi) belirtmenize olanak sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Application.StartupUri%2A>.

**Uygulama çerçevesini etkinleştir** ayarı silinirse, bu liste **Başlangıç nesnesi** olur ve hem form hem de sınıfları veya modülleri ile gösterir `Sub Main` .

**Başlangıç nesnesi** , uygulama yüklenirken çağrılacak giriş noktasını tanımlar. Genellikle bu, uygulamanızdaki ana forma veya `Sub Main` uygulama başladığında çalışması gereken yordama ayarlanır. Sınıf kitaplıklarının bir giriş noktası olmadığından, bu özellik için yalnızca seçeneği **(None)** olur. Daha fazla bilgi için bkz. [/Main](/dotnet/visual-basic/reference/command-line-compiler/main). Programlı olarak bu özelliğe erişmek için bkz <xref:VSLangProj.ProjectProperties.StartupObject%2A> ..

### <a name="icon"></a>Simge

Program simgenizin olarak kullanmak istediğiniz. ico dosyasını ayarlar. **\<Browse...>** Var olan bir grafiğe gitmek için seçin. Daha fazla bilgi için bkz. [/Win32Icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (veya [/Win32ıcon (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)). Programlı olarak bu özelliğe erişmek için bkz <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A> ..

### <a name="assembly-information"></a>Derleme bilgileri

[Derleme bilgileri Iletişim kutusunu](../../ide/reference/assembly-information-dialog-box.md)göstermek için bu düğmeye tıklayın.

### <a name="enable-application-framework"></a>Uygulama çerçevesini etkinleştir

Projenin uygulama çerçevesini kullanıp kullanmayacağını belirtir. Bu seçeneğin ayarı **başlangıç formu** / **Başlangıç nesnesinde** bulunan seçenekleri etkiler.

Bu onay kutusu işaretliyse, uygulamanız standart kullanır `Sub Main` . bu onay kutusunun belirlenmesi, **Windows uygulama çerçevesi özellikleri** bölümündeki özellikleri sağlar ve ayrıca bir başlangıç formu seçmenizi gerektirir.

Bu onay kutusu silinirse, uygulamanız `Sub Main` **Başlangıç formunda** belirttiğiniz özel kullanımı kullanır. Bu durumda, bir başlangıç nesnesi ( `Sub Main` bir yöntemde veya bir sınıfta özel) ya da bir form belirtebilirsiniz. ayrıca, **Windows application framework özellikler** bölümündeki seçenekler kullanılamaz hale gelir.

### <a name="view-windows-settings"></a>Windows Ayarlar görüntüle

*App. manifest* dosyasını oluşturmak ve açmak için bu düğmeye tıklayın. Visual Studio, bu dosyayı uygulama için bildirim verileri oluşturmak üzere kullanır. Ardından `<requestedExecutionLevel>` *app. manifest* içindeki etiketini AŞAĞıDAKI şekilde değiştirerek UAC istenen yürütme düzeyini ayarlayın:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce, bir düzeyi `asInvoker` veya sanallaştırılmış modda (bildirim oluşturma olmadan) kullanılabilir. Sanallaştırılmış modu belirtmek için, tüm etiketi App. manifest öğesinden kaldırın.

bildirim oluşturma hakkında daha fazla bilgi için bkz. [Windows Vista 'da ClickOnce dağıtımı](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Windows uygulama çerçevesi özellikleri

aşağıdaki ayarlar **Windows uygulama çerçevesi özellikleri** bölümünde bulunur. Bu seçenekler yalnızca **uygulama çerçevesini etkinleştir** onay kutusu seçiliyse kullanılabilir.

> [!TIP]
> bunu izleyen bölümde, Windows Presentation Foundation (WPF) uygulamalarına özgü **Windows uygulama çerçevesi özellikleri** açıklanmaktadır.

### <a name="enable-xp-visual-styles"></a>XP görsel stillerini etkinleştir

*Windows xp temaları* olarak da bilinen Windows xp görsel stillerini etkinleştirilir veya devre dışı bırakır. Windows XP görsel stilleri, yuvarlatılmış köşeler ve dinamik renklerle denetimleri sağlar. Varsayılan değer etkindir.

### <a name="make-single-instance-application"></a>Tek örnekli uygulama oluştur

Kullanıcıların uygulamanın birden çok örneğini çalıştırmasını engellemek için bu onay kutusunu işaretleyin. Bu onay kutusunun varsayılan ayarı *temizlenir* ve bu, uygulamanın birden çok örneğinin çalıştırılmasına izin verir. Daha fazla bilgi için, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> olayına bakın.

### <a name="save-mysettings-on-shutdown"></a>Şunu Kaydet. Ayarlar kapatılırken

`My.Settings`Kullanıcılar bilgisayarlarını kapatdıkları zaman uygulamanın ayarlarının kaydedileceğini belirtmek için bu onay kutusunu işaretleyin. Varsayılan ayar etkindir. Bu seçenek devre dışıysa, çağırarak uygulama ayarlarını el ile kaydedebilirsiniz `My.Settings.Save` .

### <a name="authentication-mode"></a>Kimlik doğrulaması modu

şu anda oturum açmış kullanıcıyı tanımlamak için Windows kimlik doğrulamasının kullanımını belirtmek üzere **Windows** (varsayılan) seçeneğini belirleyin. Bu bilgileri, nesnesini kullanarak çalışma zamanında alabilirsiniz `My.User` . varsayılan Windows kimlik doğrulama yöntemlerini kullanmak yerine, kullanıcıların kimliğini doğrulamak için kendi kodunuzu sağlayacağınızı **uygulama tanımlı** ' yı seçin.

### <a name="shutdown-mode"></a>Kapalı modu

Başlangıç formu kapandığında uygulamanın çıkış ' ı kapattığında, diğer formlar açık olsa bile, uygulamanın çıkış **biçimini seçin (** varsayılan). Son  form kapatıldığında veya ne zaman `My.Application.Exit` ya da `End` deyimin açıkça çağrılışında uygulamanın çıkış yapmak için son form kapandığında öğesini seçin.

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
