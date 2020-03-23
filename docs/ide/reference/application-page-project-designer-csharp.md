---
title: C# proje özelliklerinin uygulama sayfası
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ef9a38fc13d0d9c9f6b912f4cb2b83971d105c29
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595832"
---
# <a name="application-page-project-designer-c"></a>Uygulama Sayfası, Proje Tasarımcısı (C#)

Projenin uygulama ayarlarını ve özelliklerini belirtmek için **Proje Tasarımcısı'nın** **Uygulama** sayfasını kullanın.

**Uygulama** sayfasına erişmek için **Çözüm Gezgini'nde**bir proje düğümü **(Çözüm** düğümü değil) seçin. Ardından menü çubuğunda **Project** > **Properties'i** seçin. Proje **Tasarımcısı** göründüğünde, **Uygulama** sekmesini tıklatın.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Genel Uygulama Ayarları

Aşağıdaki seçenekler, uygulama için genel ayarları yapılandırmanızı sağlar.

**Montaj adı**

Derleme bildirimini tutacak çıktı dosyasının adını belirtir. Bu özelliğideğiştirmek, **Çıktı Adı** özelliğini de değiştirir.

Ayrıca [/out (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option)kullanarak komut satırından bu değişikliği yapabilirsiniz.

Bu özelliğe programlı olarak <xref:VSLangProj.ProjectProperties.AssemblyName%2A>erişmek için bkz.

**Varsayılan ad alanı**

Projeye eklenen dosyaların temel ad alanını belirtir.

Kodunuzda ad alanları oluşturma hakkında daha fazla bilgi için [ad alanına](/dotnet/csharp/language-reference/keywords/namespace) bakın.

Bu özelliğe programlı olarak <xref:VSLangProj.ProjectProperties.RootNamespace%2A>erişmek için bkz.

**Hedef Çerçeve**

.NET sürümünü belirtir ve uygulama nın hedeflediğini belirtir. Bu seçenek, .NET'in bilgisayarınızda hangi sürümlerinin yüklendiğine bağlı olarak farklı değerlere sahip olabilir.

.NET Framework projeleri için varsayılan değer, projeyi oluşturduğunuzda belirttiğiniz hedef çerçeveyle eşleşir.

.NET Core'u hedefleyen bir proje için kullanılabilir sürümler aşağıdaki gibi görünebilir:

![Bir .NET Core projesi için hedef çerçeve sürümleri](../media/application-target-framework.png)

> [!NOTE]
> [Önkoşul İletişim Kutusu'nda](../../ide/reference/prerequisites-dialog-box.md) listelenen ön koşul paketleri, iletişim kutusunu ilk açtığınız anda otomatik olarak ayarlanır. Daha sonra projenin hedef çerçevesini değiştirirseniz, yeni hedef çerçeveyle eşleşecek ön koşulları el ile seçmeniz gerekir.

Daha fazla bilgi için çerçeve [hedefleme genel bakış'a](../../ide/visual-studio-multi-targeting-overview.md)bakın.

**Çıkış türü**

Oluşturmak için uygulama türünü belirtir. Değerler proje türüne bağlı olarak farklıdır. Örneğin, konsol **uygulaması** projesi nde, çıktı türü olarak **Windows Uygulaması,** **Konsol Uygulaması**veya **Sınıf Kitaplığı** belirtebilirsiniz.

Bir web uygulama projesi için **Sınıf Kitaplığı**belirtmeniz gerekir.

**Çıktı türü** özelliği hakkında daha fazla bilgi için bkz. [/hedef (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).

Bu özelliğe programlı olarak nasıl erişilisi hakkında bilgi için bkz. <xref:VSLangProj.ProjectProperties.OutputType%2A>

**Otomatik oluşturma bağlama yönlendirmeleri**

Uygulamanız veya bileşenleri aynı derlemenin birden fazla sürümüne başvuruyorsa, bağlama yönlendirmeleri projenize eklenir. Proje dosyasındaki bağlama yönlendirmelerini el ile tanımlamak istiyorsanız, **Otomatik oluşturma bağlama yönlendirmelerini**seçin.

Yeniden yönlendirme hakkında daha fazla bilgi için [bkz.](/dotnet/framework/configure-apps/redirect-assembly-versions)

**Başlangıç nesnesi**

Uygulama yüklendiğinde çağrılacak giriş noktasını tanımlar. Genellikle bu, uygulamanızdaki ana forma veya uygulama `Main` başladığında çalışması gereken yordama ayarlanır. Sınıf kitaplıklarında bir giriş noktası olmadığından, bu özellik için tek seçenekleri **(Ayarlı değil)**'dir.

Varsayılan olarak, bir WPF uygulama projesinde, bu seçenek **(Ayarlanmaz)** olarak ayarlanır. Diğer seçenek \[projeadı].App. Bir WPF projesinde, uygulama başladığında başlangıç URI'sini bir Kullanıcı Arabirimi kaynağı yüklenmesi için ayarlamanız gerekir. Bunu yapmak için, projenizdeki *Application.xaml* dosyasını `StartupUri` açın ve özelliği *projenizdeki Window1.xaml*gibi bir *.xaml* dosyasına ayarlayın. Kabul edilebilir kök öğelerin <xref:System.Windows.Application.StartupUri%2A>listesi için bkz. Ayrıca projede `public static void Main()` bir sınıfta bir yöntem tanımlamanız gerekir. Bu **sınıf, Başlangıç nesnesi** listesinde *ProjectName.ClassName*olarak görünür. Daha sonra başlangıç nesnesi olarak sınıfı seçebilirsiniz.

Daha fazla bilgi için [/main (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) bakın. Bu özelliğe programlı olarak <xref:VSLangProj.ProjectProperties.StartupObject%2A>erişmek için bkz.

**Montaj Bilgileri**

Bu [düğme, Derleme Bilgileri](../../ide/reference/assembly-information-dialog-box.md) iletişim kutusunu açar.

## <a name="resources"></a>Kaynaklar

**Kaynaklar** seçenekleri, uygulamanız için kaynak ayarlarını yapılandırmanıza yardımcı olur.

**Simge ve bildirim**

Varsayılan olarak, bu radyo düğmesi seçilir ve **Simge** ve **Bildirim** seçenekleri etkinleştirilir. Bu, kendi simgenizi seçmenize veya farklı bildirim oluşturma seçenekleri seçmenize olanak tanır. Proje için bir kaynak dosyası sağlamadığınız sürece bu radyo düğmesini seçili bırakın.

**Simge**

Program simgeniz olarak kullanmak istediğiniz *.ico* dosyasını ayarlar. Varolan bir grafiğe göz atmak veya istediğiniz dosyanın adını yazmak için **Gözat'ı** tıklatın. Daha fazla bilgi için [/win32icon (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) numaralı kullanıcıya bakın.

Bu özelliğe programlı olarak <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>erişmek için bkz.

Simge oluşturma hakkında bilgi [için, simgeler için Resim düzenleyicisi'ne](/cpp/windows/image-editor-for-icons)bakın.

**Bildirim**

Uygulama Windows Vista'da Kullanıcı Hesabı Denetimi (UAC) altında çalıştığında bir bildirim oluşturma seçeneği seçer. Bu seçenek aşağıdaki değerlere sahip olabilir:

- **Varsayılan ayarlarla bildirimi gömme.** Visual Studio'nun Windows Vista'da çalışma biçimini destekler, bu da güvenlik bilgilerini uygulamanın yürütülebilir `AsInvoker`dosyasına katıştırmaktır ve bunu `requestedExecutionLevel` belirtir. Bu varsayılan seçenektir.

- **Bir bildirim olmadan uygulama oluşturun.** Bu yöntem *sanallaştırma*olarak bilinir. Önceki uygulamalarla uyumluluk için bu seçeneği kullanın.

- **Özellikler\app.manifest**. Bu seçenek ClickOnce veya Registration-Free COM tarafından dağıtılan uygulamalar için gereklidir. ClickOnce dağıtımını kullanarak bir uygulama yayımlarsanız, **Bildirim** otomatik olarak bu seçeneklere ayarlanır.

**Kaynak dosyası**

Proje için bir kaynak dosyası sağlarken bu radyo düğmesini seçin. Bu seçeneğin seçilmesi **Simge** ve **Bildirim** seçeneklerini devre dışı kılabilir.

Projeye win32 kaynak dosyası eklemek için bir yol adı girin veya Gözat düğmesini **(...**) kullanın.

Daha fazla bilgi için [.NET uygulamaları için kaynak dosyaları oluştur'a](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)bakın.
