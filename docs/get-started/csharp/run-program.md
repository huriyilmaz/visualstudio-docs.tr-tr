---
title: Program nasıl çalıştırılabilen (C#)
description: Visual Studio'da C# programının nasıl çalıştırılacaklarına ilişkin başlangıç kılavuzu.
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
ms.openlocfilehash: ee28bde6de10006ccfdc5175cca629ad9d1590d0
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649648"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Nasıl: Visual Studio'da C# programı çalıştırın

Bir programı çalıştırmak için yapmanız gerekenler, nereden başladığınız, ne tür bir program, uygulama veya hizmet olduğuna ve hata ayıklayıcının altında çalıştırmak isteyip istemediğinize bağlıdır. En basit durumda, Visual Studio'da açık bir projeniz olduğunda, **ctrl**+**F5** **(Hata ayıklama olmadan başlat)** veya **F5** **(Hata ayıklama ile başlayın)** tuşuna basarak veya ana Visual Studio araç çubuğundaki yeşil oka **(Başlat Düğmesi)** basarak projeyi oluşturun ve çalıştırın.

![Ekran görüntüsü gösterim düğmesi](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Projeden başlayarak

C# projeniz *(.csproj* dosyası) varsa, çalıştırılabilir bir programsa çalıştırabilirsiniz. Bir proje yöntemi olan bir `Main` C# dosyası içeriyorsa ve çıktısı çalıştırılabilir (EXE) ise, büyük olasılıkla başarılı bir şekilde inşa edilirse çalışacaktır.

Visual Studio'daki bir projede programınız için kod zaten varsa, projeyi açın. Projeyi açmak için Windows Dosya Gezgini'nden veya Visual Studio'dan *.csproj'a* çift tıklayın veya dokunun, **projeyi***(.csproj*) dosyasını bulmak için proje aç'ı seçin ve proje dosyasını seçin.

Visual Studio'daki projeler yüklendikten sonra **Ctrl**+**F5** **(Hata ayıklamadan başlat)** tuşuna basın veya programı çalıştırmak için Visual Studio araç çubuğundaki yeşil **Başlat** düğmesini kullanın.  Birden çok proje varsa, yönteme `Main` sahip olan Başlangıç projesi olarak ayarlanmalıdır. Başlangıç projesini ayarlamak için, proje düğümüne sağ tıklayın ve **başlangıç projesi olarak Ayarla'yı**seçin.

![Başlangıç projesini ayarlama](media/set-as-startup-project.png)

Visual Studio projenizi oluşturmaya ve çalıştırmaya çalışır.  Yapı hataları varsa, **Çıktı** penceresindeki yapı çıktısını ve **Hata Listesi** penceresindeki hataları görürsünüz.

Yapı başarılı olursa, uygulama proje türüne uygun şekilde çalışır. Konsol uygulamaları terminal penceresinde çalışır, Windows masaüstü uygulamaları yeni bir pencerede başlar, web uygulamaları tarayıcıda başlar (IIS Express tarafından barındırılır) vb.

## <a name="starting-from-code"></a>Koddan başlayarak

Kod kaydından, kod dosyasından veya az sayıda dosyadan başlıyorsanız, öncelikle çalıştırmak istediğiniz kodun güvenilir bir kaynaktan olduğundan ve çalıştırılabilir bir program olduğundan emin olun. Bir `Main` yöntemi varsa, büyük olasılıkla Visual Studio'da çalışmak üzere bir proje oluşturmak için Konsol Uygulaması şablonu kullanabilirsiniz çalıştırılabilir bir program olarak tasarlanmıştır.

### <a name="code-listing-for-a-single-file"></a>Tek bir dosya için kod listesi

Visual Studio'yu başlatın, boş bir C# konsol uytun projesini açın, projede bulunan .cs dosyasındaki tüm kodu seçin ve silin. Ardından, kodunuzun içeriğini .cs dosyasına yapıştırın. Kodu yapıştırdığınızda, daha önce orada olan kodun üzerine yazın veya silin. Dosyayı özgün kodla eşleşecek şekilde yeniden adlandırın.

### <a name="code-listings-for-a-few-files"></a>Birkaç dosya için kod listeleri

Visual Studio'yu başlatın, boş bir C# konsol uytun projesini açın, projede bulunan .cs dosyasındaki tüm kodu seçin ve silin. Ardından, ilk kod dosyasının içeriğini .cs dosyasına yapıştırın. Dosyayı özgün kodla eşleşecek şekilde yeniden adlandırın. 

İkinci bir dosya için, proje için kısayol menüsünü açmak için **Solution Explorer'daki** proje düğümüne sağ tıklayın ve **Varolan Öğe> Ekle'yi** (veya **Shift**+**Alt**+**A**tuş kombinasyonunu kullanın) seçin ve kod dosyalarını seçin.

### <a name="multiple-files-on-disk"></a>Diskte birden çok dosya

1. Uygun türde yeni bir proje oluşturun (emin değilseniz C# **Console App'i** kullanın).

2. Proje düğümüne sağ tıklayın, dosyaları seçmek ve projenize aktarmak için**Varolan Öğe** **ekle** > se.  

### <a name="starting-from-a-folder"></a>Bir klasörden başlayarak

Çok sayıda dosyadan oluşan bir klasörle çalışırken, önce bir proje veya çözüm olup olmadığına bakın.  Program Visual Studio ile oluşturulduysa, bir proje dosyası veya çözüm dosyası bulmanız gerekir. *.csproj* uzantılı veya .sln uzantılı dosyaları arayın ve Windows Dosya Gezgini'nde visual studio'da açmak için dosyalarından birine çift tıklayın. Bkz. [Visual Studio çözümünden veya projesinden başlayarak.](#starting-from-a-project)

Kod başka bir geliştirme ortamında geliştirilmiş gibi bir proje dosyanız yoksa, Visual Studio'da Açık klasör yöntemini kullanarak üst düzey **klasörü** açın. Bkz. [Proje veya çözüm olmadan kod geliştirin.](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="starting-from-a-github-or-azure-devops-repo"></a>GitHub veya Azure DevOps repo'sundan başlayarak

Çalıştırmak istediğiniz kod GitHub'da veya Azure DevOps repo'sundaysa, projeyi doğrudan repo'dan açmak için Visual Studio'yu kullanabilirsiniz. Bkz. [Bir repodan proje aç.](../tutorial-open-project-from-repo.md)

## <a name="run-the-program"></a>Programı çalıştırma

Programı başlatmak için, ana Visual Studio araç çubuğundaki yeşil oka **(Başlat** düğmesi) basın veya programı çalıştırmak için **F5** veya **Ctrl**+**F5** tuşuna basın. **Başlat** düğmesini kullandığınızda hata ayıklamanın altında çalışır.  Visual Studio, projenizdeki kodu oluşturmaya ve çalıştırmaya çalışır.  Eğer başarılı olursa, harika! Ama değilse, başarılı bir şekilde inşa etmek için nasıl bazı fikirler için okumaya devam edin.

## <a name="troubleshooting"></a>Sorun giderme

Kodunuzda hatalar olabilir, ancak kod doğruysa, ancak diğer derlemelere veya NuGet paketlerine bağlıysa veya .NET'in farklı bir sürümünü hedeflemek üzere yazılmışsa, kolayca düzeltebilirsiniz.

### <a name="add-references"></a>Referans ekleme

Düzgün bir şekilde oluşturmak için kodun doğru olması ve kitaplıklara veya diğer bağımlılıklara doğru başvuruların ayarlanması gerekir. Kırmızı kıvrımlı çizgilere ve **programda** herhangi bir hata olup olmadığını görmek için Hata Listesi'ne bakabilirsiniz. Çözülmemiş adlarla ilgili hatalar görüyorsanız, büyük olasılıkla bir başvuru veya kullanma yönergesi veya her ikisini de eklemeniz gerekir. Kod herhangi bir derlemeye veya NuGet paketine başvuruyorsa, bu başvuruları projeye eklemeniz gerekir.

Visual Studio eksik başvuruları belirlemenize yardımcı olmaya çalışır. Bir ad çözülmediğinde, düzenleyicide bir ampul simgesi görünür. Ampulü tıklattığınızda, sorunu nasıl çözeceğimiz le ilgili bazı öneriler görebilirsiniz. Düzeltmeler şu şekilde olabilir:

- kullanma yönergesi ekleme
- bir derlemeye bir başvuru eklemek veya
- NuGet paketi yükleyin.

#### <a name="missing-using-directive"></a>Yönergeyi kullanma eksik

Örneğin, aşağıdaki ekranda, çözülmemiş adı `using System;` `Console`çözmek için kod dosyasının başlangıcına eklemeyi seçebilirsiniz:

![Kullanma yönergesi eklemek için ampulekran görüntüsü](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Eksik montaj başvurusu

.NET başvuruları derlemeler veya NuGet paketleri şeklinde olabilir. Genellikle, kaynak kodu bulursanız, yayımcı veya yazar hangi derlemelerin gerekli olduğunu ve kodun hangi paketlere bağlı olduğunu açıklar. Projeye el ile başvuru eklemek **için, Çözüm Gezgini'ndeki** **Başvuru** düğümüne sağ tıklayın, **Başvuru Ekle'yi**seçin ve gerekli derlemeyi bulun.

![Referans Ekle menüsünün ekran görüntüsü](media/add-reference.png)

[Başvuru yöneticisini kullanarak ekleme yönergelerini](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)izleyerek derlemeler bulabilir ve referanslar ekleyebilirsiniz.

#### <a name="missing-nuget-package"></a>Eksik NuGet paketi

Visual Studio eksik bir NuGet paketini algılarsa, bir ampul görüntülenir ve yükleme seçeneği sunar:

![Paketi yüklemek için ampul ekran görüntüsü](media/lightbulb-add-package.png)

Bu sorunu çözmezse ve Visual Studio paketi bulamazsa, çevrimiçi aramayı deneyin. [Bkz. Visual Studio'da bir NuGet paketi yükleyin ve kullanın.](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

## <a name="use-the-right-version-of-net"></a>.NET'in doğru sürümünü kullanma

.NET Framework'ün farklı sürümleri bir dereceye kadar geriye dönük uyumluluğa sahip olduğundan, daha yeni bir çerçeve herhangi bir değişiklik yapmadan eski bir çerçeve için yazılmış kod çalıştırabilir. Ancak, bazen belirli bir çerçeveyi hedeflemeniz gerekir. Zaten yüklü değilse,.NET Framework veya .NET Core'un belirli bir sürümünü yüklemeniz gerekebilir. Bkz. [Görsel Stüdyo'da değiştirin.](../../install/modify-visual-studio.md)

Hedef çerçeveyi değiştirmek için [bkz.](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version) Daha fazla bilgi için sorun [giderme .NET Framework hedefleme hatalarına](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)bakın.

## <a name="next-steps"></a>Sonraki adımlar

[Visual Studio IDE hoşgeldiniz](../visual-studio-ide.md)okuyarak Visual Studio geliştirme ortamını keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[İlk C# uygulamanızı oluşturma](tutorial-console.md)
