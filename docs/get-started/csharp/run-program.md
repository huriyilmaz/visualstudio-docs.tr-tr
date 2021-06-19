---
title: Program çalıştırma (C#)
description: Visual Studio'da C# programı çalıştırmaya Visual Studio.
ms.custom: vs-acquisition, get-started
ms.date: 10/16/2019
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
ms.openlocfilehash: e20caabb55e65801224177168f5c936f81402bbd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385233"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Nasıl Visual Studio'de C# programı çalıştırma

Bir programı çalıştırmak için ne yapmak istediğiniz, ne tür bir program, uygulama veya hizmet olduğu ve hata ayıklayıcısı altında çalıştırmak isteyip istemediklere bağlıdır. En basit durumda, Visual Studio'de açık bir projeniz olduğunda, **Ctrl** F5 ( Hata ayıklama olmadan başlat ) veya + **F5** (  Hata ayıklamaile başla) tuşlarına basarak veya ana araç çubuğundaki yeşil oka ( Başlat Düğmesi ) basarak projeyi Visual Studio çalıştırın.

![Başlat düğmesini gösteren ekran görüntüsü](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Bir projeden başlama

Bir C# projeniz (*.csproj* dosyası) varsa, değiştirilebilir bir programsa bunu çalıştırabilirsiniz. Bir proje, yöntemine sahip bir C# dosyası içeriyorsa ve çıktısı yürütülebilir (EXE) ise, büyük olasılıkla `Main` başarıyla derlemesi varsa bu dosya çalıştırılabilir.

Program kodunuz projesinde zaten varsa Visual Studio açın. Projeyi açmak için Windows Dosya Gezgini veya Visual Studio'dan *.csproj* dosyasına çift tıklayın veya dokunun, Proje **aç'ı** seçin, projeyi (*.csproj*) bulmak için gözatın ve proje dosyasını seçin.

Projeler Visual Studio sonra **Ctrl** F5 ( Hata ayıklama olmadan başlat) tuşlarına basın veya programı çalıştırmak için Visual Studio araç çubuğundaki yeşil +  Başlat düğmesini kullanın.   Birden çok proje varsa, yöntemine `Main` sahip olan proje başlangıç projesi olarak ayar gerekir. Başlangıç projesini ayarlamak için bir proje düğümüne sağ tıklayın ve Başlangıç projesi olarak **ayarla'yı seçin.**

![Başlangıç projesini ayarlama](media/set-as-startup-project.png)

Visual Studio derlemeye ve çalıştırmaya çalışır.  Derleme hataları varsa Çıkış penceresinde derleme çıkışını **ve** hataları Hata Listesi **penceresinde** görebilirsiniz.

Derleme başarılı olursa uygulama, proje türüne uygun bir şekilde çalışır. Konsol uygulamaları bir terminal penceresinde çalışır, Windows masaüstü uygulamaları yeni bir pencerede başlar, web uygulamaları tarayıcıda başlar (IIS Express tarafından barındırılan) ve daha pek çok şey.

## <a name="starting-from-code"></a>Koddan başlama

Bir kod listesi, kod dosyası veya az sayıda dosyadan başlıyorsanız, önce çalıştırmak istediğiniz kodun güvenilir bir kaynaktan olduğundan ve çalıştırılabilir bir program olduğundan emin olun. Yöntemi varsa, büyük olasılıkla Konsol Uygulaması şablonunu kullanarak bir proje oluşturmak ve bu şablonla birlikte çalışmak için çalıştırılabilir bir `Main` program olarak Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Tek bir dosya için kod listesi

İlk Visual Studio, boş bir C# konsol projesi açın, .cs dosyasındaki projede yer alan tüm kodu seçin ve silin. Ardından kodunuzun içeriğini .cs dosyasına yapıştırın. Kodu yapıştırarak daha önce orada olan kodun üzerine yazın veya silin. Dosyayı özgün kodla eş olacak şekilde yeniden adlandırır.

### <a name="code-listings-for-a-few-files"></a>Birkaç dosya için kod listeleri

İlk Visual Studio, boş bir C# konsol projesi açın, .cs dosyasındaki projede yer alan tüm kodu seçin ve silin. Ardından, ilk kod dosyasının içeriğini .cs dosyasına yapıştırın. Dosyayı özgün kodla eş olacak şekilde yeniden adlandırır. 

İkinci bir dosya için Çözüm Gezgini'daki proje  düğümüne sağ tıklar, projenin kısayol menüsünü açın ve Mevcut Öğe ekle'yi **>'yi** seçin (veya **Shift** Alt A tuş bileşimini kullanın) ve kod dosyalarını +  + seçin.

### <a name="multiple-files-on-disk"></a>Diskte birden çok dosya

1. Uygun türde yeni bir proje oluşturun (emin **değilken** C# Konsol Uygulamasını kullanın).

2. Proje düğümüne sağ tıklayın, dosyaları **seçmek ve** bunları projenize içeri  >   aktarın.  

### <a name="starting-from-a-folder"></a>Klasörden başlama

Çok sayıda dosya içeren bir klasörle çalışırken öncelikle bir proje veya çözüm olup ola bir şey olup ola bir bakın.  Program yeni bir Visual Studio, bir proje dosyası veya çözüm dosyası bulmanız gerekir. *.csproj uzantısına* veya .sln uzantısına sahip dosyaları arama ve Windows Dosya Gezgini'de dosyalardan birini çift tıklar ve dosyaları Visual Studio. Bkz. [Bir Visual Studio çözümünden veya projesinden başlama.](#starting-from-a-project)

Kod başka bir geliştirme ortamında geliştirilmiş gibi bir proje dosyanız yoksa, klasör aç yöntemini kullanarak  üst düzey klasörü Visual Studio. Bkz. [Projeler veya çözümler olmadan kod geliştirme.](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="starting-from-a-github-or-azure-devops-repo"></a>GitHub'dan veya Azure DevOps başlayarak

Çalıştırmak istediğiniz kod GitHub'da veya Azure DevOps depoda ise projeyi doğrudan Visual Studio açmak için Visual Studio kullanabilirsiniz. Bkz. [Bir repodan proje açma.](../tutorial-open-project-from-repo.md)

## <a name="run-the-program"></a>Programı çalıştırma

Programı başlatmak için ana araç çubuğundaki **yeşil** ok ( Başlat düğmesine) Visual Studio veya F5 veya **Ctrl** **F5** tuşlarına basarak programı +  çalıştırın. Başlat düğmesini **kullanarak** hata ayıklayıcısı altında çalışır.  Visual Studio projenize kodu derlemeye ve çalıştırmaya çalışır.  Bu başarılı olursa, harika! Ancak, yoksa, başarıyla derlemeye nasıl alın hakkında bazı fikirler için okumaya devam edin.

## <a name="troubleshooting"></a>Sorun giderme

Kodunuz hata içeriyor olabilir, ancak kod doğruysa, ancak yalnızca bazı diğer derlemelere veya NuGet paketlerine bağlıysa veya farklı bir .NET sürümünü hedeflemek için yazılmışsa, bunu kolayca düzeltebilirsiniz.

### <a name="add-references"></a>Başvuru ekleme

Doğru şekilde derlemek için kodun doğru olması ve kitaplıklara veya diğer bağımlılıklara doğru başvuruların ayarlanmış olması gerekir. Derlemeden ve çalıştırmadan önce bile programın  herhangi bir hata olup olduğunu görmek için kırmızı çizgilere ve Hata Listesi'ne bakabilirsiniz. Çözümlenmemiş adlarla ilgili hatalar görüyorsanız, büyük olasılıkla bir başvuru, kullanma yönergesi veya her ikisini birden eklemeniz gerekir. Kod herhangi bir derlemeye veya NuGet paketine başvurursa, bu başvuruları projeye eklemeniz gerekir.

Visual Studio eksik başvuruları tanımlamanıza yardımcı olmak için çalışır. Bir ad çözümlenmemişse düzenleyicide bir ampul simgesi görünür. Ampule tıklarsanız sorunu nasıl çözeceğime ilişkin bazı önerilere bakabilirsiniz. Düzeltmeler şöyle olabilir:

- using yönergesi ekleme
- bir derlemeye başvuru ekleme veya
- bir NuGet paketi yükleyin.

#### <a name="missing-using-directive"></a>Using yönergesi eksik

Örneğin, aşağıdaki ekranda çözümlenmemiş adı çözümlemek için kod dosyasının `using System;` başlangıcına eklemeyi `Console` seçebilirsiniz:

![using yönergesi eklemek için ampulün ekran görüntüsü](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Eksik derleme başvurusu

.NET başvuruları derlemeler veya NuGet paketleri şeklinde olabilir. Genellikle kaynak kodu bulursanız yayımcı veya yazar hangi derlemelerin gerekli olduğunu ve kodun hangi paketlere bağlı olduğunu açıklar. Projeye el ile başvuru eklemek için, projedeki Başvurular düğümüne sağ **tıklayın, Çözüm Gezgini** Ekle'yi **seçin** ve gerekli derlemeyi bulun. 

![Başvuru Ekle menüsünün ekran görüntüsü](media/add-reference.png)

Başvuru yöneticisini kullanarak başvuru ekleme veya kaldırma'daki yönergeleri izleyerek derlemeleri bulabilir ve [başvuru ekleyin.](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)

#### <a name="missing-nuget-package"></a>Eksik NuGet paketi

Eksik Visual Studio NuGet paketini algılarsa, bir ampul görünür ve bunu yükleme seçeneği sunar:

![Paket yüklemek için ampulün ekran görüntüsü](media/lightbulb-add-package.png)

Bu, sorunu çözene ve Visual Studio paketi bulamazsa, çevrimiçi olarak aramayı deneyin. Bkz. [Visual Studio'de NuGet paketi yükleme ve kullanma.](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

## <a name="use-the-right-version-of-net"></a>.NET'in doğru sürümünü kullanma

Uygulamanın farklı sürümleri .NET Framework bir ölçüde geriye dönük uyumluluka sahip olduğundan, daha yeni bir çerçeve herhangi bir değişiklik yapmadan eski bir çerçeve için yazılmış kodu çalıştırabilir. Ancak bazen belirli bir çerçeveyi hedeflemeniz gerekir. Henüz yüklenmemişse, .NET Framework veya .NET Core'un belirli bir sürümünü yüklemeniz gerekir. Bkz. [Visual Studio.](../../install/modify-visual-studio.md)

Hedef çerçeveyi değiştirmek için [bkz. Hedef çerçeveyi değiştirme.](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version) Daha fazla bilgi için [bkz. .NET Framework giderme.](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio IDE'ye hoş [geldiniz'i okuyarak Visual Studio keşfedin.](../visual-studio-ide.md)

## <a name="see-also"></a>Ayrıca bkz.

[İlk C# uygulamanızı oluşturma](tutorial-console.md)
