---
title: Program çalıştırma (C#)
description: Acemi kullanıcının Visual Studio bir C# programının nasıl çalıştırılacağını gösteren kılavuz.
ms.custom: vs-acquisition, get-started
ms.date: 08/24/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e2a5e2997a15f3d91c9a12d3aff5c1d1e31aff90
ms.sourcegitcommit: aef3e3f99e022675d339b7fe381cb37202be5be2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2021
ms.locfileid: "122785929"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Nasıl yapılır: Visual Studio bir C# programı çalıştırma

Bir programı çalıştırmak için yapmanız gerekenler, ne başladığınıza, ne tür bir program, uygulama veya hizmete sahip olduğunu ve hata ayıklayıcı altında çalıştırmak isteyip istemediğinizi belirtir. en basit durumda, Visual Studio ' de bir proje açtığınızda, **Ctrl** + **F5** (**hata ayıklama olmadan başlat**) veya **F5** (**hata ayıklama ile başla**) tuşlarına basarak veya ana Visual Studio araç çubuğunda yeşil oka (**başlat düğmesi**) basın.

![Başlat düğmesini gösteren ekran görüntüsü](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Bir projeden başlayarak

Bir C# projeniz (*. csproj* dosyası) varsa, bu bir çalıştırılabilir programdır. Bir proje, yöntemi olan bir C# dosyası içeriyorsa `Main` ve çıktısı bir çalıştırılabilir (exe) ise, büyük olasılıkla başarılı olursa çalışır.

programınızın zaten Visual Studio bir projede kodu varsa projeyi açın. projeyi açmak için Windows dosya gezgini 'nden *. csproj* öğesine çift tıklayın veya dokunun ya da Visual Studio, proje **aç**' ı seçin, proje (*. csproj*) dosyasını bulun ve proje dosyasını seçin.

projeler Visual Studio yüklendikten sonra **Ctrl** + **F5** tuşuna basın (**hata ayıklama olmadan başlat**) veya programı çalıştırmak için Visual Studio araç çubuğundaki yeşil **başlat** düğmesini kullanın.  Birden çok proje varsa, yöntemi içeren bir `Main` Başlangıç projesi olarak ayarlanmalıdır. Başlangıç projesini ayarlamak için, proje düğümüne sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

![Başlangıç projesini ayarla](media/set-as-startup-project.png)

Visual Studio projenizi derleyip çalıştırmaya çalışır.  Yapı hataları varsa, **Çıkış** penceresinde yapı çıkışını ve **hata listesi** penceresindeki hataları görürsünüz.

Yapı başarılı olursa uygulama, proje türü için uygun bir şekilde çalışır. konsol uygulamaları bir terminal penceresinde çalışır, Windows masaüstü uygulamaları yeni bir pencerede başlar, web uygulamaları tarayıcıda başlar (IIS Express tarafından barındırılır) ve bu şekilde devam eder.

## <a name="starting-from-code"></a>Koddan başlayarak

Kod listesinden, kod dosyasından veya az sayıda dosyadan başlatıyorsanız, önce çalıştırmak istediğiniz kodun güvenilen bir kaynaktan geldiğinden ve bir çalıştırılabilir program olduğundan emin olun. Bir yöntemi varsa, bu, bir `Main` proje oluşturmak için bir proje oluşturmak üzere konsol uygulaması şablonunu kullanabileceğiniz bir çalıştırılabilir program olarak tasarlanmıştır Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Tek bir dosya için kod Listeleme

Visual Studio başlatın, boş bir C# konsol projesi açın, projede zaten bulunan. cs dosyasındaki tüm kodu seçin ve silin. Daha sonra, kodunuzun içeriğini. cs dosyasına yapıştırın. Kodu yapıştırdığınızda, daha önce yaptığınız kodu üzerine yazın veya silin. Dosyayı özgün kodla eşleşecek şekilde yeniden adlandırın.

### <a name="code-listings-for-a-few-files"></a>Birkaç dosya için kod listeleri

Visual Studio başlatın, boş bir C# konsol projesi açın, projede zaten bulunan. cs dosyasındaki tüm kodu seçin ve silin. Sonra, ilk kod dosyasının içeriğini. cs dosyasına yapıştırın. Dosyayı özgün kodla eşleşecek şekilde yeniden adlandırın. 

İkinci bir dosya için, proje için kısayol menüsünü açmak üzere **Çözüm Gezgini** içindeki proje düğümüne sağ tıklayın ve **> var olan öğeyi Ekle** ' yi (veya tuş birleşimini **SHIFT** + **alt** + **a**' yı kullanın) seçin ve kod dosyalarını seçin.

### <a name="multiple-files-on-disk"></a>Diskte birden çok dosya

1. Uygun türde yeni bir proje oluşturun (emin değilseniz C# **konsol uygulamasını** kullanın).

2. Proje düğümüne sağ tıklayın,   >  dosyaları seçmek ve bunları projenize aktarmak için **Mevcut öğeyi** ekleyin.  

### <a name="starting-from-a-folder"></a>Bir klasörden başlayarak

Birçok dosyanın bir klasörüyle çalışırken, önce bir proje veya çözüm olup olmadığını görün.  program Visual Studio ile oluşturulduysa bir proje dosyası veya çözüm dosyası bulmanız gerekir. *. csproj* uzantısına veya. sln uzantısına sahip dosyaları arayın ve Windows dosya gezgini ' nde, Visual Studio açmak için bunlardan birine çift tıklayın. bkz. [Visual Studio bir çözümden veya projeden başlatma](#starting-from-a-project).

Bir proje dosyanız yoksa (örneğin, kod başka bir geliştirme ortamında geliştirildiği gibi), en üst düzey klasörü Visual Studio içindeki **klasörü aç** metodunu kullanarak açın. Bkz. [Proje veya çözüm olmadan kod geliştirme](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>bir GitHub veya Azure DevOps deposundan başlayarak

çalıştırmak istediğiniz kod GitHub veya bir Azure DevOps deposunda ise, projeyi doğrudan depodan açmak için Visual Studio kullanabilirsiniz. Bkz. [bir depodan bir proje açma](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Programı çalıştırma

programı başlatmak için ana Visual Studio araç çubuğunda yeşil oka (**başlat** düğmesi) basın veya **f5** ya da **Ctrl** + **f5** tuşlarına basarak programı çalıştırın. **Başlat** düğmesini kullandığınızda, hata ayıklayıcı altında çalışır.  Visual Studio projenizdeki kodu oluşturmaya ve çalıştırmaya çalışır.  Bu başarılı olursa harika! Aksi halde, başarıyla derlenmeye yönelik bazı fikirler için okumaya devam edin.

## <a name="troubleshooting"></a>Sorun giderme

kodunuzun hataları olabilir, ancak kod doğru olsa da, diğer derlemelere veya NuGet paketlerine bağlıdır veya .net 'in farklı bir sürümünü hedefleyecek şekilde yazılmışsa, kolayca düzeltemezsiniz.

### <a name="add-references"></a>Başvuru Ekle

Doğru şekilde derlemek için kodun doğru olması ve kitaplıklara veya diğer bağımlılıklara ayarlanmış doğru başvuruların olması gerekir. , Derlemeden ve çalıştırmadan önce, programda hata olup olmadığını görmek için kırmızı dalgalı çizgilere ve **hata listesi** bakabilirsiniz. Çözümlenmemiş adlarla ilgili hatalar görüyorsanız, muhtemelen bir başvuru ya da bir using yönergesi veya her ikisini de eklemeniz gerekir. kod herhangi bir derlemeye veya NuGet pakete başvuruyorsa, bu başvuruları projeye eklemeniz gerekir.

Visual Studio eksik başvuruları belirlemenize yardımcı olmaya çalışır. Bir ad çözülmemiş olduğunda, düzenleyicide ampul simgesi görünür. Ampul ' e tıklarsanız, sorunun nasıl düzeltileceğini öğrenmek için bazı öneriler bulabilirsiniz. Düzeltmeler şu şekilde olabilir:

- using yönergesi ekleme
- bir derlemeye başvuru ekleyin veya
- NuGet paketini yükler.

#### <a name="missing-using-directive"></a>Using yönergesi eksik

Örneğin, aşağıdaki ekranda, `using System;` çözümlenmemiş adı çözümlemek için kod dosyasının başlangıcına eklemeyi seçebilirsiniz `Console` :

![Using yönergesi eklemek için ampul ekran görüntüsü](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Eksik bütünleştirilmiş kod başvurusu

.net başvuruları derlemeler veya NuGet paketleri biçiminde olabilir. Genellikle, kaynak kodu bulursanız, yayımcı veya yazar hangi derlemelerin gerekli olduğunu ve kodun hangi paketlere bağımlı olduğunu açıklayacak. Bir projeye el ile başvuru eklemek için **Çözüm Gezgini** **Başvurular** düğümüne sağ tıklayın, **Başvuru Ekle**' yi seçin ve gerekli derlemeyi bulun.

![Başvuru Ekle menüsünün ekran görüntüsü](media/add-reference.png)

[Başvuru Yöneticisi 'ni kullanarak başvuru ekleme veya kaldırma](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)bölümündeki yönergeleri izleyerek derlemeleri bulabilir ve başvurular ekleyebilirsiniz.

#### <a name="missing-nuget-package"></a>NuGet paketi eksik

Visual Studio eksik bir NuGet paketi algılarsa, bir ampul görünür ve size bunu yüklemenize yönelik bir seçenek sunar:

![Paketin yükleneceği ampul ekran görüntüsü](media/lightbulb-add-package.png)

bu sorun çözülmezse ve Visual Studio paketi bulamıyorsa, çevrimiçi aramayı deneyin. bkz. [Visual Studio NuGet paketini yükleyip kullanma](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>.NET sürümünün doğru sürümünü kullanın

.NET Framework farklı sürümlerinin geriye dönük uyumluluk olduğu için, daha yeni bir çerçeve, hiçbir değişiklik yapılmadan eski bir çerçeve için yazılmış kodu çalıştırabilir. Ancak bazen belirli bir çerçeveyi hedeflemek zorunda olabilirsiniz. zaten yüklenmemişse, .NET Framework veya .net Core 'un belirli bir sürümünü yüklemeniz gerekebilir. Bkz. [Visual Studio değiştirme](../../install/modify-visual-studio.md).

Hedef Framework 'ü değiştirmek için bkz. [hedef Framework 'Ü değiştirme](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). daha fazla bilgi için bkz. [.NET Framework hedefleme hatalarını giderme](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Sonraki adımlar

[Visual Studio ıde 'ye hoş geldiniz](../visual-studio-ide.md)'i okuyarak Visual Studio geliştirme ortamını keşfedebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

[İlk C# uygulamanızı oluşturma](tutorial-console.md)
