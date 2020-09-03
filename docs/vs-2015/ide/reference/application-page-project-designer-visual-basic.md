---
title: Uygulama sayfası, proje Tasarımcısı (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: 8cec9fea-cd92-47ff-88dd-7c928f0b4a74
caps.latest.revision: 68
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 893647303b493ea633caf076658edbdcf0664ccc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850847"
---
# <a name="application-page-project-designer-visual-basic"></a>Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projenin uygulama ayarlarını ve özelliklerini belirtmek için proje Tasarımcısı ' nın **uygulama** sayfasını kullanın.

 **Uygulama** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü ( **çözüm** düğümünü değil) seçin. Ardından, menü çubuğunda **Proje**, **Özellikler** ' i seçin. Proje Tasarımcısı göründüğünde **uygulama** sekmesine tıklayın.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="general-application-settings"></a>Genel uygulama ayarları
 Aşağıdaki seçenekler bir uygulama için genel ayarları yapılandırmanıza olanak tanır.

 **Bütünleştirilmiş kod adı** Derleme bildirimini içeren çıkış dosyasının adını belirtir. Bu özelliği değiştirirseniz, **Çıkış adı** özelliği de değişecektir. Ayrıca, [/Out (Visual Basic)](https://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae)kullanarak bir komut isteminde bu değişikliği yapabilirsiniz. Bu özelliğe programlı bir şekilde erişme hakkında daha fazla bilgi için bkz <xref:VSLangProj.ProjectProperties.AssemblyName%2A> ..

 **Kök ad alanı** Projedeki tüm dosyalar için temel ad alanını belirtir. Örneğin, **kök ad alanını** olarak ayarlarsanız `Project1` ve `Class1` kodunuzda herhangi bir ad alanı dışında bir alanınız varsa, ad alanı olur `Project1.Class1` . Kodda bir ad alanında varsa `Class2` `Order` , ad alanı olur `Project1.Order.Class2` .

 **Kök ad alanını**temizlerseniz, kodda projenizin ad alanı yapısını belirtebilirsiniz.

> [!NOTE]
> Bir [Namespace Ifadesinde](https://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2)Global anahtar sözcüğünü kullanırsanız, projenizin kök ad alanından bir ad alanı tanımlayabilirsiniz. **Kök ad alanını**temizlerseniz, `Global` üst düzey ad alanı haline gelir ve bu, `Global` bir deyimdeki anahtar kelimesinin gereksinimini ortadan kaldırır `Namespace` . Daha fazla bilgi için [Visual Basic ad alanları](https://msdn.microsoft.com/library/cffac744-ab8c-4f1f-ba50-732c22ab4b88)Içindeki "ad alanı deyimlerine genel anahtar sözcük" başlığına bakın.

 Kodunuzda ad alanlarını oluşturma hakkında daha fazla bilgi için bkz. [Namespace deyimleri](https://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2).

 Kök ad alanı özelliği hakkında daha fazla bilgi için bkz. [/RootNamespace](https://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783).

 Bu özelliğe programlı bir şekilde erişme hakkında daha fazla bilgi için bkz <xref:VSLangProj.ProjectProperties.RootNamespace%2A> ..

 **Hedef çerçeve (tüm yapılandırma)** Uygulamanın hedeflediği .NET Framework sürümünü belirtir. Bu seçenek, bilgisayarınızda hangi .NET Framework sürümlerinin yüklü olduğuna bağlı olarak farklı değerlere sahip olabilir.

 Varsayılan değer, **Yeni proje** iletişim kutusunda belirttiğiniz hedef Framework ile eşleşir.

> [!NOTE]
> [Önkoşullar Iletişim kutusunda](../../ide/reference/prerequisites-dialog-box.md) listelenen önkoşul paketleri, iletişim kutusunu ilk kez açtığınızda otomatik olarak ayarlanır. Projenin hedef çerçevesini daha sonra değiştirirseniz, yeni hedef Framework 'ü eşleştirmek için önkoşulları el ile belirtmeniz gerekir.

 Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) hedefleme ve [Visual Studio çoklu hedefleme 'ye genel bakış](../../ide/visual-studio-multi-targeting-overview.md).

 **Uygulama türü** Oluşturulacak uygulamanın türünü belirtir. [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]Uygulamalar Için **Windows Mağazası uygulaması**, **sınıf kitaplığı**veya **winmd dosyası**belirtebilirsiniz. Diğer çoğu uygulama türü için, **Windows uygulaması**, **konsol uygulaması**, **sınıf kitaplığı**, **Windows hizmeti**veya **Web denetim kitaplığı**belirtebilirsiniz.

 Bir Web uygulaması projesi için **sınıf kitaplığı**belirtmeniz gerekir.

 **Winmd dosyası** seçeneğini belirtirseniz türler, herhangi bir Windows çalışma zamanı programlama diliyle yansıtıluygulanabilir. Projenin çıkışını bir WinMD dosyası olarak paketleyerek, bir uygulamayı birden fazla dilde kodlayarak kod birlikte çalışır ve aynı dilde yazmış olursunuz. Uygulamalar dahil Windows Çalışma Zamanı kitaplıklarını hedefleyen çözümler için **winmd dosyası** seçeneğini kullanabilirsiniz [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] . Daha fazla bilgi için bkz. [C# ve Visual Basic Windows çalışma zamanı bileşenleri oluşturma](https://msdn.microsoft.com/library/windows/apps/br230301(v=VS.85).aspx).

> [!NOTE]
> Windows Çalışma Zamanı, bu tür bir dilde yerel nesneler olarak görünecek şekilde proje türlerine sahip olabilir. Örneğin, Windows Çalışma Zamanı etkileşimde bulunan JavaScript uygulamaları bunu bir JavaScript nesneleri kümesi olarak kullanır ve C# uygulamaları kitaplığı bir .NET nesneleri koleksiyonu olarak kullanır. Projenin çıkışını bir WinMD dosyası olarak paketleyerek, Windows Çalışma Zamanı kullandığı teknolojinin avantajlarından yararlanabilirsiniz.

 **Uygulama türü** özelliği hakkında daha fazla bilgi için bkz. [/target (Visual Basic)](https://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c). Bu özelliğe programlı bir şekilde erişme hakkında daha fazla bilgi için bkz <xref:VSLangProj.ProjectProperties.OutputType%2A> ..

 **Simge** Program simgenizin olarak kullanmak istediğiniz. ico dosyasını ayarlar. **\<Browse...>** Var olan bir grafiğe gitmek için seçin. Daha fazla bilgi için bkz. [/Win32Icon](https://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) (veya [/Win32ıcon (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138)). Programlı olarak bu özelliğe erişmek için bkz <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A> ..

 **Başlangıç formu/başlangıç nesnesi/başlangıç URI 'si** Uygulamanın başlangıç formunu veya giriş noktasını belirtir.

 **Uygulama çerçevesini etkinleştir** seçilirse (varsayılan), bu liste **başlangıç formu** olarak belirlenir ve yalnızca form gösterir çünkü uygulama çerçevesi nesneleri değil yalnızca başlangıç formlarını destekler.

 Proje bir WPF tarayıcı uygulamasıdır, bu liste **Başlangıç URI 'si**ve varsayılan olarak **Sayfa1. xaml**' dir. **Başlangıç URI** listesi, uygulama başladığında uygulamanın görüntülediği Kullanıcı arabirimi KAYNAĞıNı (XAML öğesi) belirtmenize olanak sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Application.StartupUri%2A>.

 **Uygulama çerçevesini etkinleştir** ayarı silinirse, bu liste **Başlangıç nesnesi** olur ve hem form hem de sınıfları veya modülleri ile gösterir `Sub Main` .

 **Başlangıç nesnesi** , uygulama yüklenirken çağrılacak giriş noktasını tanımlar. Genellikle bu, uygulamanızdaki ana forma veya `Sub Main` uygulama başladığında çalışması gereken yordama ayarlanır. Sınıf kitaplıklarının bir giriş noktası olmadığından, bu özellik için yalnızca seçeneği **(None)** olur. Daha fazla bilgi için bkz. [/Main](https://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0). Programlı olarak bu özelliğe erişmek için bkz <xref:VSLangProj.ProjectProperties.StartupObject%2A> ..

 **Derleme bilgileri** [Derleme bilgileri Iletişim kutusunu](../../ide/reference/assembly-information-dialog-box.md)göstermek için bu düğmeye tıklayın.

 **Uygulama çerçevesini etkinleştir** Projenin uygulama çerçevesini kullanıp kullanmayacağını belirtir. Bu seçeneğin ayarı **başlangıç formu** / **Başlangıç nesnesinde**bulunan seçenekleri etkiler.

 Bu onay kutusu işaretliyse, uygulamanız standart kullanır `Sub Main` . Bu onay kutusu seçildiğinde, **Windows uygulama çerçevesi özellikleri** bölümündeki Özellikler etkinleştirilir ve ayrıca bir başlangıç formu seçmeniz gerekir.

 Bu onay kutusu silinirse, uygulamanız `Sub Main` **Başlangıç formunda**belirttiğiniz özel kullanımı kullanır. Bu durumda, bir başlangıç nesnesi ( `Sub Main` bir yöntemde veya bir sınıfta özel) ya da bir form belirtebilirsiniz. Ayrıca, **Windows Application Framework Özellikler** bölümündeki seçenekler kullanılamaz hale gelir.

 **Windows ayarlarını görüntüleme** App. manifest dosyasını oluşturmak ve açmak için bu düğmeye tıklayın. Visual Studio, uygulama için bildirim verileri oluşturmak üzere bu dosyayı kullanır. Ardından `<requestedExecutionLevel>` app. manifest içindeki etiketini aşağıdaki şekilde DEĞIŞTIREREK UAC istenen yürütme düzeyini ayarlayın:

 `<requestedExecutionLevel level="asInvoker" />`

 ClickOnce, bir düzeyi `asInvoker` veya sanallaştırılmış modda (bildirim oluşturma olmadan) kullanılabilir. Sanallaştırılmış modu belirtmek için, tüm etiketi App. manifest öğesinden kaldırın.

 Bildirim oluşturma hakkında daha fazla bilgi için bkz. [Windows Vista 'Da ClickOnce dağıtımı](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Windows uygulama çerçevesi özellikleri
 **Windows uygulama çerçevesi özellikleri** bölümünde aşağıdaki ayarlar bulunur. Bu seçenekler yalnızca **uygulama çerçevesini etkinleştir** onay kutusu seçiliyse kullanılabilir. Bunu izleyen bölümde Windows Presentation Foundation (WPF) uygulamaları için **Windows uygulama çerçevesi özellikleri** ayarları açıklanmaktadır.

 **XP görsel stillerini etkinleştir** *WINDOWS XP temaları*olarak da BILINEN Windows XP görsel stillerini etkinleştirilir veya devre dışı bırakır. Windows XP görsel stilleri, yuvarlatılmış köşeler ve dinamik renklerle denetimleri sağlar. Varsayılan değer etkindir. Windows XP görsel stilleri hakkında daha fazla bilgi için bkz. [WINDOWS XP özellikleri ve Windows Forms denetimleri](https://msdn.microsoft.com/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)).

 **Tek örnekli uygulama oluştur** Kullanıcıların uygulamanın birden çok örneğini çalıştırmasını engellemek için bu onay kutusunu işaretleyin. Bu onay kutusunun varsayılan ayarı temizlenir. Bu ayar, uygulamanın birden çok örneğinin çalıştırılmasına izin verir.

 **My. Settings 'ı kapatmadan kaydet** `My.Settings` Kullanıcılar bilgisayarlarını kapatdıkları zaman uygulamanın ayarlarının kaydedileceğini belirtmek için bu onay kutusunu işaretleyin. Varsayılan ayar etkindir. Bu seçenek devre dışıysa, çağırarak uygulama ayarlarını el ile kaydedebilirsiniz `My.Settings.Save` .

 **Kimlik doğrulama modu** Şu anda oturum açmış kullanıcıyı tanımlamak için Windows kimlik doğrulamasının kullanımını belirtmek üzere **Windows** (varsayılan) seçeneğini belirleyin. Bu bilgileri, nesnesini kullanarak çalışma zamanında alabilirsiniz `My.User` . Varsayılan Windows kimlik doğrulama yöntemlerini kullanmak yerine, kullanıcıların kimliğini doğrulamak için kendi kodunuzu sağlayacağınızı **uygulama tanımlı** ' yı seçin.

 **Kapalı modu** Başlangıç formu kapandığında uygulamanın çıkış ' ı kapattığında, diğer formlar açık olsa bile, uygulamanın çıkış **biçimini seçin (** varsayılan). Son **When last form closes** form kapatıldığında veya ne zaman `My.Application.Exit` ya da `End` deyimin açıkça çağrılışında uygulamanın çıkış yapmak için son form kapandığında öğesini seçin.

 Açıkça kapatıldığında uygulamanın çıkış yaptığınızda çıkış olduğunu belirtmek için **Açık Kapat '** ı seçin `Shutdown` .

 Son pencere kapandığında veya açıkça çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **son pencere Kapat '** ı seçin `Shutdown` . Bu varsayılan ayardır.

 Ana pencere kapandığında veya açıkça çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **ana pencerede Kapat '** ı seçin `Shutdown` .

 **Giriş ekranı** Giriş ekranı olarak kullanmak istediğiniz formu seçin. Daha önce bir form veya şablon kullanarak bir giriş ekranı oluşturmuş olmanız gerekir. Varsayılan değer **(yok)**.

 **Uygulama olaylarını görüntüle** Uygulama çerçevesi olayları,, ve için olay yazabileceğiniz bir olay kodu dosyası göstermek için bu düğmeye tıklayın `Startup` `Shutdown` `UnhandledException` `StartupNextInstance` `NetworkAvailabilityChanged` . Ayrıca, belirli uygulama çerçevesi yöntemlerini geçersiz kılabilirsiniz. Örneğin, giriş ekranının görüntüleme davranışını geçersiz kılarak değiştirebilirsiniz `OnInitialize` .

### <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Windows Presentation Foundation (WPF) uygulamaları için Windows uygulama çerçevesi özellikleri
 Aşağıdaki ayarlar, proje Windows Presentation Foundation bir uygulama olduğunda **Windows uygulama çerçevesi özellikleri** bölümünde bulunur. Bu seçenekler yalnızca **uygulama çerçevesini etkinleştir** onay kutusu seçiliyse kullanılabilir. Bu tabloda listelenen seçenekler yalnızca WPF uygulamaları veya WPF tarayıcı uygulamaları için kullanılabilir. Bunlar WPF Kullanıcı denetimi veya özel denetim kitaplıkları için kullanılamaz.

 **Kapalı modu** Bu özellik yalnızca Windows Presentation Foundation uygulamalar için geçerlidir.

 Açıkça kapatıldığında uygulamanın çıkış yaptığınızda çıkış olduğunu belirtmek için **Açık Kapat '** ı seçin <xref:System.Windows.Application.Shutdown%2A> .

 Son pencere kapandığında veya açıkça çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **son pencere Kapat '** ı seçin <xref:System.Windows.Application.Shutdown%2A> . Bu varsayılan ayardır.

 Ana pencere kapandığında veya açıkça çağırdığınızda uygulamanın çıkış olduğunu belirtmek için **ana pencerede Kapat '** ı seçin <xref:System.Windows.Application.Shutdown%2A> .

 Bu ayarı kullanma hakkında daha fazla bilgi için bkz. <xref:System.Windows.Application.Shutdown%2A>

 **Xaml düzenleme** XAML düzenleyicisinde uygulama tanım dosyasını (Application. xaml) açmak ve değiştirmek için bu düğmeye tıklayın. Bu düğmeye tıkladığınızda, Application. xaml uygulama tanımı düğümünde açılır. Kaynakları tanımlama gibi belirli görevleri gerçekleştirmek için bu dosyayı düzenlemeniz gerekebilir. Uygulama tanımı dosyası yoksa, proje Tasarımcısı bir tane oluşturur.

 **Uygulama olaylarını görüntüle** `Application` Kısmi sınıf dosyasını (Application. xaml. vb) bir kod düzenleyicisinde göstermek için bu düğmeye tıklayın. Dosya yoksa, proje Tasarımcısı uygun sınıf adı ve ad alanıyla bir tane oluşturur.

 <xref:System.Windows.Application>Nesne, belirli uygulama durumu değişiklikleri oluştuğunda (örneğin, uygulama başlangıcında veya kapatılırken) olaylar oluşturur. Bu sınıfın sunduğu olayların tam listesi için bkz <xref:System.Windows.Application> .. Bu olaylar, kısmi sınıfın Kullanıcı kodu bölümünde işlenir `Application` .

## <a name="see-also"></a>Ayrıca Bkz.
[Office çözümlerinde kod yazma](https://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0) [uygulama özelliklerini yönetme](../../ide/application-properties.md)
