---
title: Uygulama sayfası, proje Tasarımcısı (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: f13701a8-4e2e-4474-9d60-bb43decbe0c1
caps.latest.revision: 61
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2bf9c64a55f6f3b49cb1e0a50fa532f276394dac
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851996"
---
# <a name="application-page-project-designer-c"></a>Uygulama Sayfası, Proje Tasarımcısı (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projenin uygulama ayarlarını ve özelliklerini belirtmek için **Proje Tasarımcısı** ' nın **uygulama** sayfasını kullanın.

 **Uygulama** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü ( **çözüm** düğümünü değil) seçin. Ardından, menü çubuğunda **Proje**, **Özellikler** ' i seçin. Proje Tasarımcısı göründüğünde **uygulama** sekmesine tıklayın.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="general-application-settings"></a>Genel uygulama ayarları
 Aşağıdaki seçenekler, uygulamanın genel ayarlarını yapılandırmanızı sağlar.

 **Bütünleştirilmiş kod adı** Derleme bildirimini tutacak çıkış dosyasının adını belirtir. Bu özelliğin değiştirilmesi, **Çıkış adı** özelliğini de değiştirecek. Ayrıca, [/Out (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5)kullanarak komut satırından da bu değişikliği yapabilirsiniz. Bu özelliğe program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

 **Varsayılan ad alanı** Projeye eklenen dosyalar için temel ad alanını belirtir.

 Kodunuzda ad alanları oluşturma hakkında daha fazla bilgi için bkz. [ad alanı](https://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) .

 Bu özelliğe program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

 **Hedef çerçeve** Uygulamanın hedeflediği .NET Framework sürümünü belirtir. Bu seçenek, bilgisayarınızda hangi .NET Framework sürümlerinin yüklü olduğuna bağlı olarak farklı değerlere sahip olabilir.

 Varsayılan olarak, değer **Yeni proje** iletişim kutusunda seçtiğiniz hedef çerçeve ile aynıdır.

> [!NOTE]
> [Önkoşullar Iletişim kutusunda](../../ide/reference/prerequisites-dialog-box.md) listelenen önkoşul paketleri, iletişim kutusunu ilk açışınızda otomatik olarak ayarlanır. Projenin hedef çerçevesini daha sonra değiştirirseniz, yeni hedef Framework 'ü eşleştirmek için önkoşulları el ile seçmeniz gerekir.

 Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) hedefleme ve [Visual Studio çoklu hedefleme 'ye genel bakış](../../ide/visual-studio-multi-targeting-overview.md).

 **Uygulama türü** Oluşturulacak uygulamanın türünü belirtir. [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] uygulamalar için **Windows Mağazası uygulaması**, **sınıf kitaplığı**veya **winmd dosyası**belirtebilirsiniz. Diğer çoğu uygulama türü için, **Windows uygulaması**, **konsol uygulaması**, **sınıf kitaplığı**, **Windows hizmeti**veya **Web denetim kitaplığı**belirtebilirsiniz.

 Bir Web uygulaması projesi için **sınıf kitaplığı**belirtmeniz gerekir.

 **Winmd dosyası** seçeneğini belirtirseniz türler, herhangi bir Windows çalışma zamanı programlama diliyle yansıtıluygulanabilir. Projenin çıkışını bir WinMD dosyası olarak paketleyerek, bir uygulamayı birden fazla dilde kodlayarak kod birlikte çalışır ve aynı dilde yazmış olursunuz. [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] uygulamalar dahil Windows Çalışma Zamanı kitaplıklarını hedefleyen çözümler için bu seçeneği belirtebilirsiniz. Daha fazla bilgi için bkz. [ C# ve Visual Basic Windows çalışma zamanı bileşenleri oluşturma](https://msdn.microsoft.com/library/windows/apps/br230301(v=VS.85).aspx).

> [!NOTE]
> Windows Çalışma Zamanı, bu tür bir dilde yerel nesneler olarak görünecek şekilde proje türlerine sahip olabilir. Örneğin, Windows Çalışma Zamanı etkileşimde bulunan JavaScript uygulamaları bunu bir JavaScript nesneleri kümesi olarak kullanır ve C# uygulamalar kitaplığı bir .NET nesneleri koleksiyonu olarak kullanır. Projenin çıkışını bir WinMD dosyası olarak paketleyerek, Windows Çalışma Zamanı kullandığı teknolojinin avantajlarından yararlanabilirsiniz.

 **Uygulama türü** özelliği hakkında daha fazla bilgi için bkz. [/target (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f). Bu özelliğe programlı bir şekilde erişme hakkında daha fazla bilgi için bkz. <xref:VSLangProj.ProjectProperties.OutputType%2A>.

 **Derleme bilgileri** Bu düğmeye tıkladığınızda [derleme bilgileri Iletişim kutusu](../../ide/reference/assembly-information-dialog-box.md)görüntülenir.

 **Başlangıç nesnesi** Uygulama yüklenirken çağrılacak giriş noktasını tanımlar. Genellikle bu, uygulamanızdaki ana forma veya uygulama başladığında çalışması gereken `Main` yordama ayarlanır. Sınıf kitaplıklarının bir giriş noktası olmadığından, bu özellik için yalnızca seçeneği **(ayarlanmamış)** olur.

 Varsayılan olarak, bir WPF tarayıcı uygulaması projesinde, bu seçenek **(ayarlanmadı)** . Diğer seçenek *ProjectName*. App ' dir. Bu tür bir projede, uygulama başladığında bir UI kaynağı yüklemek için başlangıç URI 'sini ayarlamanız gerekir. Bunu yapmak için, projenizdeki Application. xaml dosyasını açın ve `StartupUri` özelliğini projenizdeki bir. xaml dosyası (örneğin, Window1. xaml) olarak ayarlayın. Kabul edilebilir kök öğelerinin bir listesi için bkz. <xref:System.Windows.Application.StartupUri%2A>. Ayrıca, projedeki bir sınıfta `public static void Main()` yöntemi tanımlamanız gerekir. Bu sınıf, **Başlangıç nesnesi** listesinde *ProjectName. ClassName*olarak görünür. Ardından, başlangıç nesnesi olarak sınıfını seçebilirsiniz.

 Daha fazla bilgi için bkz. [/Main (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049) . Bu özelliğe program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

## <a name="resources"></a>Kaynaklar
 Aşağıdaki seçenekler, uygulamanın genel ayarlarını yapılandırmanızı sağlar.

 **Simge ve bildirim** Varsayılan olarak, bu radyo düğmesi seçilidir ve **simge** ve **bildirim** seçenekleri etkindir. Bu, kendi simgenizi seçmenizi veya farklı bildirim oluşturma seçeneklerini seçmenizi sağlar. Proje için bir kaynak dosyası sağlamadığınız müddetçe bu radyo düğmesini seçili bırakın.

 **Simge** Program simgenizin olarak kullanmak istediğiniz. ico dosyasını ayarlar. Var olan bir grafiğe gitmek için üç nokta düğmesine tıklayın veya istediğiniz dosyanın adını yazın. Daha fazla bilgi için bkz. [/Win32Icon (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138) . Bu özelliğe program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

 **Bildirim** Uygulama Windows Vista 'da Kullanıcı hesabı denetimi (UAC) altında çalışırken bir bildirim oluşturma seçeneği belirler. Bu seçenek aşağıdaki değerlere sahip olabilir:

- **Bildirimi varsayılan ayarlarla ekleyin**. , Uygulamanın yürütülebilir dosyasındaki güvenlik bilgilerini eklemek için `requestedExecutionLevel` `AsInvoker`olduğunu belirterek, Visual Studio 'Nun Windows Vista 'da işlem yaptığı tipik yolu destekler. Bu varsayılan seçenektir.

- **Bildirim olmadan uygulama oluşturun**. Bu yöntem *sanallaştırma*olarak bilinir. Önceki uygulamalarla uyumluluk için bu seçeneği kullanın.

- **Properties\app.manifest**. Bu seçenek, ClickOnce veya kayıtsız COM tarafından dağıtılan uygulamalar için gereklidir. ClickOnce dağıtımını kullanarak bir uygulamayı yayımlarsanız, **bildirim** otomatik olarak bu seçeneğe ayarlanır.

  **Kaynak dosyası** Proje için bir kaynak dosyası sağlıyorsanız bu radyo düğmesini seçin. Bu seçenek belirlendiğinde, **simge** ve **bildirim** seçenekleri devre dışı bırakılır.

  Bir yol adı girin veya projeye bir Win32 kaynak dosyası eklemek için ( **...** ) düğmesini kullanın.

## <a name="see-also"></a>Ayrıca Bkz.
[Office çözümlerinde kod yazma](https://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0) [uygulama özelliklerini yönetme](../../ide/application-properties.md)
