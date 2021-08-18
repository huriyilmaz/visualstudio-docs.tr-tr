---
title: C# proje özelliklerinin uygulama sayfası
description: Projenin uygulama ayarlarını ve özelliklerini belirtmek için C# Project Tasarımcısı'nın Uygulama sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: e3b369e1862dc295d4262d30709c2ee30a21854bead9e91b69fc6ca0fa726866
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357614"
---
# <a name="application-page-project-designer-c"></a>Uygulama Sayfası, Proje Tasarımcısı (C#)

Projenin **uygulama** ayarlarını ve **özelliklerini Project Tasarımcısı'nın** Uygulama sayfasını kullanın.

Uygulama sayfasına **erişmek için,** uygulamasında bir proje düğümü **(Çözüm düğümü** değil) **Çözüm Gezgini.** Ardından menü **Project**  >  **Özellikler'i** seçin. Project **Tasarımcısı** göründüğünde Uygulama **sekmesine** tıklayın.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Genel Uygulama Ayarlar

Aşağıdaki seçenekler, uygulamanın genel ayarlarını yapılandırmaya olanak sağlar.

**Derleme adı**

Derleme bildirimini tutacak çıkış dosyasının adını belirtir. Bu özelliği değiştirerek Çıkış Adı **özelliği de değişir.**

Bu değişikliği komut satırına [/out (C# Derleyici Seçenekleri) kullanarak da yapabilirsiniz.](/dotnet/csharp/language-reference/compiler-options/out-compiler-option)

Bu özelle program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.AssemblyName%2A> .

**Varsayılan ad alanı**

Projeye eklenen dosyalar için temel ad alanını belirtir.

[Kodunda](/dotnet/csharp/language-reference/keywords/namespace) ad alanları oluşturma hakkında daha fazla bilgi için bkz. ad alanı.

Bu özelle program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.RootNamespace%2A> .

**Hedef Çerçeve**

Uygulamanın hedeflemektedir .NET sürümünü belirtir. Bu seçenek, bilgisayarınızda yüklü olan .NET sürümlerine bağlı olarak farklı değerlere sahip olabilir.

Bu .NET Framework için varsayılan değer, projeyi oluşturulduğunda belirttiğiniz hedef çerçeveyle eşler.

.NET Core'a yönelik bir proje için kullanılabilir sürümler aşağıdaki gibi görünebilir:

![.NET Core projesi için hedef çerçeve sürümleri](../media/application-target-framework.png)

> [!NOTE]
> Önkoşullar İletişim Kutusunda listelenen [önkoşul](../../ide/reference/prerequisites-dialog-box.md) paketleri, iletişim kutusunu ilk kez açsanız otomatik olarak ayarlanır. Projenin hedef çerçevesini daha sonra değiştirirsiniz, yeni hedef çerçeveyle eşleşmesi için önkoşulları el ile seçmeniz gerekir.

Daha fazla bilgi için [bkz. Çerçeve hedeflemeye genel bakış.](../../ide/visual-studio-multi-targeting-overview.md)

**Çıkış türü**

Derlemek için uygulama türünü belirtir. Değerler, proje türüne bağlı olarak farklıdır. Örneğin, bir Konsol **Uygulaması projesi için** çıkış türü Windows Uygulama, **Konsol** Uygulaması veya **Sınıf Kitaplığı'nın** belirtebilirsiniz. 

Bir web uygulaması projesi için Sınıf Kitaplığını **belirtmeniz gerekir.**

Çıkış türü özelliği hakkında daha **fazla bilgi** için bkz. [/target (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).

Bu özelle program aracılığıyla nasıl erişilen hakkında bilgi için bkz. <xref:VSLangProj.ProjectProperties.OutputType%2A> .

**Bağlama yeniden yönlendirmelerini otomatik oluşturma**

Bağlama yeniden yönlendirmeleri, uygulama veya bileşenleri aynı derlemenin birden fazla sürümüne başvurursa projenize eklenir. Proje dosyasında bağlama yeniden yönlendirmelerini el ile tanımlamak için Bağlamayı otomatik oluştur yeniden **yönlendirmeleri'nin seçimini kaldırın.**

Yeniden yönlendirme hakkında daha fazla bilgi için [bkz. Derleme sürümlerini yeniden yönlendirme.](/dotnet/framework/configure-apps/redirect-assembly-versions)

**Başlangıç nesnesi**

Uygulama yüklenirken çağrıl olacak giriş noktasını tanımlar. Genellikle bu, uygulamanın ana formuna veya uygulama başlatıldığında `Main` çalışması gereken yordama ayarlanır. Sınıf kitaplıklarının bir giriş noktası yoksa, bu özellik için tek seçenekleri (Ayarlanmaz) **seçeneğidir.**

Varsayılan olarak, bir WPF uygulama projesinde bu seçenek olarak ayarlanır **(Ayarlanmaz).** Diğer seçenek ise \[ projectname].App'tir. WpF projesinde, uygulama başlatıldığında bir kullanıcı arabirimi kaynağını yüklemek için başlangıç URI'sini ayarlayabilirsiniz. Bunu yapmak için projenizin *Application.xaml* dosyasını açın ve özelliğini projeniz içinde `StartupUri` *Window1.xaml* gibi *bir .xaml* dosyasına ayarlayın. Kabul edilebilir kök öğelerin listesi için bkz. <xref:System.Windows.Application.StartupUri%2A> . Ayrıca projesinde bir `public static void Main()` sınıfta bir yöntem tanımlamanız gerekir. Bu sınıf Başlangıç nesne **listesinde** *ProjectName.ClassName olarak görünür.* Daha sonra başlangıç nesnesi olarak sınıfını seçin.

Daha [fazla bilgi için bkz. /main (C#](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) Derleyici Seçenekleri). Bu özelle program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.StartupObject%2A> .

**Derleme Bilgileri**

Bu düğme, Derleme [Bilgileri iletişim](../../ide/reference/assembly-information-dialog-box.md) kutusunu açar.

## <a name="resources"></a>Kaynaklar

Kaynaklar **seçenekleri,** uygulamanıza kaynak ayarlarını yapılandırmanıza yardımcı olur.

**Simge ve bildirim**

Varsayılan olarak, bu radyo düğmesi seçilidir ve **Simge ve** **Bildirim** seçenekleri etkinleştirilir. Bu, kendi simgenizi seçmenize veya farklı bildirim oluşturma seçenekleri seçmenize olanak sağlar. Proje için bir kaynak dosyası sağlamadıysanız bu radyo düğmesini seçili bırakın.

**Simge**

Program simgesi olarak kullanmak istediğiniz *.ico* dosyasını ayarlar. Var **olan** bir grafiği bulmak için Gözat'a tıklayın veya istediğiniz dosyanın adını yazın. Daha [fazla bilgi için bkz. /win32icon (C#](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) Derleyici Seçenekleri).

Bu özelle program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A> .

Simge oluşturma hakkında bilgi için bkz. [Simgeler için görüntü düzenleyicisi.](/cpp/windows/image-editor-for-icons)

**Bildirim**

Uygulama, Kullanıcı Hesabı Denetimi (UAC) Windows Vista üzerinde çalıştırıldıklarından bir bildirim oluşturma seçeneği seçer. Bu seçenek aşağıdaki değerlere sahip olabilir:

- **Varsayılan ayarlarla bildirim ekleme.** uygulamanın yürütülebilir dosyasına Visual Studio olarak belirterek güvenlik bilgilerini eklemek için Windows Vista üzerinde çalışma tipik bir şekilde `requestedExecutionLevel` `AsInvoker` destekler. Bu varsayılan seçenektir.

- **Bildirim olmadan uygulama oluşturun.** Bu yöntem sanallaştırma olarak *bilinir.* Önceki uygulamalarla uyumluluk için bu seçeneği kullanın.

- **Properties\app.manifest**. Bu seçenek, ClickOnce veya Registration-Free COM tarafından dağıtılan uygulamalar için gereklidir. Bir uygulamayı dağıtım sırasında ClickOnce yayımlarsanız **Bildirim** otomatik olarak bu seçenge ayarlanır.

**Kaynak dosyası**

Proje için bir kaynak dosyası sağlarken bu radyo düğmesini seçin. Bu seçeneğin seçerek Simge ve **Bildirim seçeneklerini** devre **dışı bırakmanız** gerekir.

Projeye bir Win32 kaynak dosyası eklemek için bir yol adı girin veya Gözat düğmesini (**...**) kullanın.

Daha fazla bilgi için [bkz. .NET uygulamaları için kaynak dosyaları oluşturma.](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)
