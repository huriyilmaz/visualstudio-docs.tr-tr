---
title: C# Program çalıştırma
description: Başlangıç Kılavuzu, Visual Studio 'da bir C# programın nasıl çalıştırılacağını gösterir.
ms.custom: get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2ffe52fc2bf7d05084307b4d972e45f4b1d2acdf
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76924618"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Nasıl yapılır: Visual Studio C# 'Da program çalıştırma

Bir programı çalıştırmak için yapmanız gerekenler, ne başladığınıza, ne tür bir program, uygulama veya hizmete sahip olduğunu ve hata ayıklayıcı altında çalıştırmak isteyip istemediğinizi belirtir. En basit durumda, Visual Studio 'da açık bir projeniz varsa, **Ctrl**+**F5** (**hata ayıklama olmadan Başlat**) veya **F5** (**hata ayıklama ile**başla) tuşlarına basarak oluşturun ve çalıştırın veya ana Visual Studio araç çubuğunda yeşil oka (**Start button**) basın.

![Başlat düğmesini gösteren ekran görüntüsü](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Bir projeden başlayarak

Bir C# projeniz ( *. csproj* dosyanız) varsa, bu bir çalıştırılabilir programdır. Bir proje `Main` yöntemi olan C# bir dosya içeriyorsa ve çıktısı bir ÇALıŞTıRıLABILIR (exe) ise, büyük olasılıkla başarılı olursa çalışır.

Visual Studio 'da bir projede programınızın koduna zaten sahipseniz projeyi açın. Projeyi açmak için Windows Dosya Gezgini 'nden *. csproj* öğesine çift tıklayın veya dokunun veya Visual Studio 'Dan **Proje Aç**' ı seçin, proje ( *. csproj*) dosyasını bulun ve proje dosyasını seçin.

Projeler Visual Studio 'da yüklendikten sonra, **Ctrl**+**F5** tuşuna basın (**hata ayıklama olmadan Başlat**) veya programı çalıştırmak Için Visual Studio araç çubuğundaki yeşil **Başlat** düğmesini kullanın.  Birden çok proje varsa, `Main` yöntemi olan biri başlangıç projesi olarak ayarlanmalıdır. Başlangıç projesini ayarlamak için, proje düğümüne sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

![Başlangıç projesini ayarla](media/set-as-startup-project.png)

Visual Studio, projenizi derleyip çalıştırmaya çalışır.  Yapı hataları varsa, **Çıkış** penceresinde yapı çıkışını ve **hata listesi** penceresindeki hataları görürsünüz.

Yapı başarılı olursa uygulama, proje türü için uygun bir şekilde çalışır. Konsol uygulamaları bir Terminal penceresinde çalışır, Windows Masaüstü uygulamaları yeni bir pencerede başlar, Web uygulamaları tarayıcıda başlar (IIS Express tarafından barındırılır) ve bu şekilde devam eder.

## <a name="starting-from-code"></a>Koddan başlayarak

Kod listesinden, kod dosyasından veya az sayıda dosyadan başlatıyorsanız, önce çalıştırmak istediğiniz kodun güvenilen bir kaynaktan geldiğinden ve bir çalıştırılabilir program olduğundan emin olun. Bir `Main` yöntemi varsa, bu, Visual Studio 'da onunla çalışacak bir proje oluşturmak için konsol uygulaması şablonunu kullanabileceğiniz bir çalıştırılabilir program olarak tasarlanmıştır.

### <a name="code-listing-for-a-single-file"></a>Tek bir dosya için kod Listeleme

Visual Studio 'Yu başlatın, boş C# bir konsol projesi açın, projede zaten bulunan. cs dosyasındaki tüm kodu seçin ve silin. Daha sonra, kodunuzun içeriğini. cs dosyasına yapıştırın. Kodu yapıştırdığınızda, daha önce yaptığınız kodu üzerine yazın veya silin. Dosyayı özgün kodla eşleşecek şekilde yeniden adlandırın.

### <a name="code-listings-for-a-few-files"></a>Birkaç dosya için kod listeleri

Visual Studio 'Yu başlatın, boş C# bir konsol projesi açın, projede zaten bulunan. cs dosyasındaki tüm kodu seçin ve silin. Sonra, ilk kod dosyasının içeriğini. cs dosyasına yapıştırın. Dosyayı özgün kodla eşleşecek şekilde yeniden adlandırın. 

İkinci bir dosya için, proje için kısayol menüsünü açmak üzere **Çözüm Gezgini** içindeki proje düğümüne sağ tıklayın ve **> var olan öğe Ekle** ' yi seçin (veya **tuş birleşimini+** **alt**+**a**' yı kullanın) ve kod dosyalarını seçin.

### <a name="multiple-files-on-disk"></a>Diskte birden çok dosya

1. Uygun türde yeni bir proje oluşturun (emin değilseniz C# **konsol uygulamasını** kullanın).

2. Proje düğümüne sağ tıklayın, dosyaları seçmek ve bunları projenize aktarmak için > **var olan öğeyi** **ekleyin** .  

### <a name="starting-from-a-folder"></a>Bir klasörden başlayarak

Birçok dosyanın bir klasörüyle çalışırken, önce bir proje veya çözüm olup olmadığını görün.  Program Visual Studio ile oluşturulduysa bir proje dosyası veya çözüm dosyası bulmalısınız. *. Csproj* uzantısına veya. sln uzantısına sahip dosyaları arayın ve Windows Dosya Gezgini 'Nde, Visual Studio 'da açmak için bunlardan birine çift tıklayın. Bkz. [Visual Studio çözümünden veya projesinden başlatma](#starting-from-a-project).

Kod başka bir geliştirme ortamında geliştirildiği gibi bir proje dosyanız yoksa, Visual Studio 'da **klasörü aç** yöntemini kullanarak en üst düzey klasörü açın. Bkz. [Proje veya çözüm olmadan kod geliştirme](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>GitHub veya Azure DevOps deposundan başlayarak

Çalıştırmak istediğiniz kod GitHub ' da veya bir Azure DevOps deposunda ise, projeyi doğrudan depodan açmak için Visual Studio 'Yu kullanabilirsiniz. Bkz. [bir depodan bir proje açma](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Programı çalıştırma

Programı **başlatmak için,** ana Visual Studio araç çubuğunda yeşil ok (**Başlat** düğmesi) tuşuna **basın veya programı** çalıştırmak için **F5**+F5 tuşuna basın. **Başlat** düğmesini kullandığınızda, hata ayıklayıcı altında çalışır.  Visual Studio, projenizdeki kodu oluşturmaya ve çalıştırmaya çalışır.  Bu başarılı olursa harika! Aksi halde, başarıyla derlenmeye yönelik bazı fikirler için okumaya devam edin.

## <a name="troubleshooting"></a>Sorun giderme

Kodunuzun hataları olabilir, ancak kod doğruysa, ancak başka bir derlemeye ya da NuGet paketlerine bağlıdır veya .NET 'in farklı bir sürümünü hedefleyecek şekilde yazılmışsa, kolayca düzeltemezsiniz.

### <a name="add-references"></a>Başvuru Ekle

Doğru şekilde derlemek için kodun doğru olması ve kitaplıklara veya diğer bağımlılıklara ayarlanmış doğru başvuruların olması gerekir. , Derlemeden ve çalıştırmadan önce, programda hata olup olmadığını görmek için kırmızı dalgalı çizgilere ve **hata listesi** bakabilirsiniz. Çözümlenmemiş adlarla ilgili hatalar görüyorsanız, muhtemelen bir başvuru ya da bir using yönergesi veya her ikisini de eklemeniz gerekir. Kod herhangi bir derlemeye veya NuGet paketlerine başvuruyorsa, bu başvuruları projeye eklemeniz gerekir.

Visual Studio eksik başvuruları belirlemenize yardımcı olmaya çalışır. Bir ad çözülmemiş olduğunda, düzenleyicide ampul simgesi görünür. Ampul ' e tıklarsanız, sorunun nasıl düzeltileceğini öğrenmek için bazı öneriler bulabilirsiniz. Düzeltmeler şu şekilde olabilir:

- using yönergesi ekleme
- bir derlemeye başvuru ekleyin veya
- bir NuGet paketi yükler.

#### <a name="missing-using-directive"></a>Using yönergesi eksik

Örneğin, aşağıdaki ekranda, çözümlenmemiş adı `Console`çözümlemek için kod dosyasının başlangıcına `using System;` eklemeyi seçebilirsiniz:

![Using yönergesi eklemek için ampul ekran görüntüsü](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Eksik bütünleştirilmiş kod başvurusu

.NET başvuruları derlemeler veya NuGet paketleri biçiminde olabilir. Genellikle, kaynak kodu bulursanız, yayımcı veya yazar hangi derlemelerin gerekli olduğunu ve kodun hangi paketlere bağımlı olduğunu açıklayacak. Bir projeye el ile başvuru eklemek için **Çözüm Gezgini** **Başvurular** düğümüne sağ tıklayın, **Başvuru Ekle**' yi seçin ve gerekli derlemeyi bulun.

![Başvuru Ekle menüsünün ekran görüntüsü](media/add-reference.png)

[Başvuru Yöneticisi 'ni kullanarak başvuru ekleme veya kaldırma](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)bölümündeki yönergeleri izleyerek derlemeleri bulabilir ve başvurular ekleyebilirsiniz.

#### <a name="missing-nuget-package"></a>NuGet paketi eksik

Visual Studio eksik bir NuGet paketi algılarsa, bir ampul görünür ve size bunu yüklemek için seçenek sunar:

![Paketin yükleneceği ampul ekran görüntüsü](media/lightbulb-add-package.png)

Bu sorun çözülmezse ve Visual Studio paketi bulamıyorsa, çevrimiçi aramayı deneyin. Bkz. [Visual Studio 'Da NuGet paketini yükleyip kullanma](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>.NET sürümünün doğru sürümünü kullanın

.NET Framework farklı sürümlerinin geriye dönük uyumluluk olduğu için, daha yeni bir çerçeve, hiçbir değişiklik yapılmadan eski bir çerçeve için yazılmış kodu çalıştırabilir. Ancak bazen belirli bir çerçeveyi hedeflemek zorunda olabilirsiniz. Zaten yüklenmemişse, .NET Framework veya .NET Core 'un belirli bir sürümünü yüklemeniz gerekebilir. Bkz. [Visual Studio 'Yu değiştirme](../../install/modify-visual-studio.md).

Hedef Framework 'ü değiştirmek için bkz. [hedef Framework 'Ü değiştirme](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Daha fazla bilgi için bkz. [.NET Framework Hedefleme hatalarını giderme](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio [IDE 'ye hoş geldiniz](../visual-studio-ide.md)' i okuyarak Visual Studio geliştirme ortamı 'nı gezin.

## <a name="see-also"></a>Ayrıca bkz.

[İlk C# uygulamanızı oluşturma](tutorial-console.md)
