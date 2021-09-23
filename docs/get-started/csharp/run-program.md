---
title: Program çalıştırma (C#)
description: Acemi kullanıcının Visual Studio bir C# programının nasıl çalıştırılacağını gösteren kılavuz.
ms.custom: vs-acquisition, get-started
ms.date: 09/14/2021
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
ms.openlocfilehash: f68039ca8b1bca3224766f7f2673514e3b6a2e9f
ms.sourcegitcommit: 022ac348337f77c899996ac81060a969ebfb64bb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2021
ms.locfileid: "128133796"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Nasıl yapılır: Visual Studio bir C# programı çalıştırma

Bir programı çalıştırma, ne başladığınıza, program türüne ve hata ayıklayıcı altında çalıştırmak isteyip istemediğinize bağlıdır. En basit durumda, Visual Studio içinde açık bir proje derlemek ve çalıştırmak için:

- **F5** tuşuna basın, Visual Studio menüsünde **hata ayıklama**  >  **ile başla** ' yı seçin veya Visual Studio araç çubuğunda yeşil **başlangıç** okunu ve proje adını seçin.
- ya da hata ayıklamadan çalıştırmak için, Visual Studio menüsünde, **Ctrl** + **F5** tuşuna basın veya **hata ayıklama**  >  **olmadan başlat** ' ı seçin.

::: moniker range="<=vs-2019"
![Başlat düğmesini gösteren ekran görüntüsü.](media/vs-start-button.png)
::: moniker-end
::: moniker range=">=vs-2022"
:::image type="content" source="media/vs-2022/start-button.png" alt-text="Başlat düğmesini gösteren ekran görüntüsü." border="false":::
::: moniker-end

## <a name="start-from-a-project"></a>Bir projeden başla

Bir C# projesi veya *. csproj* dosyası çalıştırılabilir bir programdır. Proje, yöntemi olan bir C# dosyası içeriyorsa `Main` ve çıktısı bir çalıştırılabilir veya *.exe* dosyası ise, büyük olasılıkla başarılı bir şekilde oluşturulmasından sonra çalışır.

1. program kodunuz zaten bir Visual Studio projesinde ise projeyi açın. bunu yapmak için Windows dosya gezgini ' nde *. csproj* dosyasına çift tıklayabilir veya dokunabilir veya Visual Studio **bir projeyi aç** ' ı seçerek *. csproj* dosyasını bulun ve dosyayı seçin.

1. proje Visual Studio yüklendikten sonra, Visual Studio çözümünüz birden fazla proje içeriyorsa, projeyi `Main` başlangıç projesi olarak yöntemiyle ayarladığınızdan emin olun. başlangıç projesini ayarlamak için **Çözüm Gezgini** proje adına veya düğümüne sağ tıklayın ve bağlam menüsünden **başlangıç Project olarak ayarla** ' yı seçin.

   ::: moniker range="<=vs-2019"
   ![Başlangıç projesinin ayarlanmasını gösteren ekran görüntüsü.](media/set-as-startup-project.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   :::image type="content" source="media/vs-2022/set-startup-project.png" alt-text="Başlangıç projesinin ayarlanmasını gösteren ekran görüntüsü." border="false":::
   ::: moniker-end

1. Programı çalıştırmak için **CTRL** + **F5** tuşuna basın, üstteki menüden hata **Ayıkla**  >  **Başlat** ' ı seçin veya yeşil **Başlat** düğmesini seçin. 

   Visual Studio projenizi derleyip çalıştırmaya çalışır. Visual Studio ekranının alt tarafında, derleme çıktısı **çıkış** penceresinde görünür ve tüm derleme hataları **Hata Listesi** penceresinde görünür.

   Yapı başarılı olursa, uygulama proje türü için uygun şekilde çalışır. konsol uygulamaları, bir terminal penceresinde çalışır Windows masaüstü uygulamaları yeni bir masaüstü penceresinde başlar ve web uygulamaları, IIS Express tarafından barındırılan bir tarayıcıda çalışır.

## <a name="start-from-code"></a>Koddan Başlat

Kod listesinden, kod dosyasından veya az sayıda dosyadan başlatırsanız, önce kodun güvenilen bir kaynaktan çalıştırılabilir program olduğundan emin olun. Yöntemi olan herhangi bir uygulama `Main` , büyük olasılıkla bir çalıştırılabilir programdır. Visual Studio ' de uygulamayla çalışacak bir proje oluşturmak için konsol uygulaması şablonunu kullanabilirsiniz.

### <a name="code-listing-for-a-single-file"></a>Tek bir dosya için kod Listeleme

1. Visual Studio başlatın ve boş bir C# konsol uygulaması projesi açın.
1. Project *. cs* dosyasındaki tüm kodu kod listelemesi veya dosyanızın içeriğiyle değiştirin.
1. Proje *. cs* dosyasını kod dosyası adınızla eşleşecek şekilde yeniden adlandırın.

### <a name="several-code-listings-or-files-on-disk"></a>Disk üzerindeki birçok kod listesi veya dosya

1. Visual Studio başlatın ve uygun türde yeni bir proje oluşturun. Emin değilseniz C# **konsol uygulamasını** kullanın.
1. Yeni projede, proje kod dosyasındaki tüm kodu ilk kod listelemesi veya dosyanızın içeriğiyle değiştirin.
1. Proje kodu dosyasını kod dosyası adınızla eşleşecek şekilde yeniden adlandırın.
1. Kalan her kod dosyası için:
   1. **Çözüm Gezgini** ' de proje düğümüne sağ tıklayın ve varolan öğe **Ekle**' yi seçin  >  veya projeyi seçip **SHIFT** + **alt** + **A**'ya basın.
   1. Projeye içeri aktarmak için kod dosyasına gidin ve dosyayı seçin.

### <a name="several-files-in-a-folder"></a>Bir klasördeki çeşitli dosyalar

Çok sayıda dosya içeren bir klasörünüz varsa, önce bir proje veya çözüm dosyası denetleyin. Visual Studio oluşturduğu programlarda proje ve çözüm dosyaları vardır. Windows dosya gezgini ' nde *. csproj* veya *. sln* uzantılı dosyaları arayın. Visual Studio açmak için *. csproj* dosyasına çift tıklayın. bkz. [Visual Studio bir çözümden veya projeden başla](#start-from-a-project).

Kod başka bir geliştirme ortamındaysanız proje dosyası yoktur. Visual Studio **klasörü aç**' a tıklayarak klasörü açın  >   . Bkz. [Proje veya çözüm olmadan kod geliştirme](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="start-from-a-github-or-azure-devops-repo"></a>bir GitHub veya Azure DevOps deposundan başla

çalıştırmak istediğiniz kod bir GitHub veya Azure DevOps deposa, projeyi doğrudan depodan açmak için Visual Studio kullanabilirsiniz. Bkz. [bir depodan bir proje açma](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Programı çalıştırma

programı oluşturmaya başlamak için Visual Studio araç çubuğundaki yeşil **başlat** düğmesine basın veya **f5** ya da **Ctrl** + **f5** tuşlarına basın. **Başlat** düğmesi veya **F5** kullanımı, programı hata ayıklayıcı altında çalıştırır.

Visual Studio projenizdeki kodu oluşturmaya ve çalıştırmaya çalışır. Bir derleme başarılı olmazsa, projenin başarıyla derlenme hakkında bazı fikirler için aşağıdaki bölümlere bakın.

## <a name="troubleshooting"></a>Sorun giderme

Kodunuzun hataları olabilir. ya da kod doğru olabilir, ancak eksik derlemelere veya NuGet paketlerine göre veya .net 'in farklı bir sürümünü hedeflemelidir. Bu durumlarda, derlemeyi kolayca düzelmeyebilirsiniz.

### <a name="add-references"></a>Başvuru Ekle

Doğru şekilde derlemek için kodun doğru olması ve kitaplıklara veya diğer bağımlılıklara doğru başvuruları olması gerekir. **Hata listesi** koddaki veya girdilerindeki kırmızı dalgalı alt çizgiler, programı derleyip çalıştırmadan önce bile hataları gösterir. Hatalar çözümlenmemiş adlarla ilişkilendirilmesiyle muhtemelen bir başvuru veya `using` yönerge eklemeniz ya da her ikisini de yapmanız gerekir. kod, eksik derlemelere veya NuGet paketlerine başvuruyorsa, bu başvuruları projeye eklemeniz gerekir.

Visual Studio eksik başvuruları belirlemenize yardımcı olmaya çalışır. Bir ad çözülmemiş olduğunda, düzenleyicide ampul simgesi görünür. Sorunu gidermeye yönelik önerileri görmek için ampulü seçin. Düzeltmeler şu şekilde olabilir:

- Using yönergesi ekleyin.
- Bir derlemeye başvuru ekleyin.
- NuGet paketini yükler.

#### <a name="add-a-using-directive"></a>Using yönergesi ekleme

Eksik yönerge örneği aşağıda verilmiştir `using` . `using System;`Çözümlenmemiş adı çözümlemek için kod dosyasının başlangıcına ekleyebilirsiniz `Console` :

::: moniker range="<=vs-2019"
![Bir using yönergesi eklemek için ampul ekran görüntüsü.](media/name-does-not-exist2.png)
::: moniker-end
::: moniker range=">=vs-2022"
:::image type="content" source="media/vs-2022/missing-using-directive.png" alt-text="Bir using yönergesi eklemek için ampul ekran görüntüsü." border="false":::
::: moniker-end

#### <a name="add-an-assembly-reference"></a>Derleme başvurusu ekleme

.net başvuruları derlemeler veya NuGet paketleri olabilir. Kaynak kodunda, yayımcı veya yazar genellikle kodun gerektirdiği derlemeleri ve hangi paketlere bağımlı olduğunu açıklar. Bir projeye el ile başvuru eklemek için, **Çözüm Gezgini** ' deki **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin. **Başvuru Yöneticisi**'nde gerekli derlemeyi bulun ve ekleyin.

::: moniker range="<=vs-2019"
![Başvuru Ekle menüsünün ekran görüntüsü.](media/add-reference.png)
::: moniker-end
::: moniker range=">=vs-2022"
:::image type="content" source="media/vs-2022/add-reference.png" alt-text="Başvuru Ekle menüsünün ekran görüntüsü." border="false":::
::: moniker-end

[Başvuru Yöneticisi 'ni kullanarak başvuru ekleme veya kaldırma](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)bölümündeki yönergeleri izleyerek derlemeleri bulabilir ve başvurular ekleyebilirsiniz.

#### <a name="add-a-nuget-package"></a>NuGet paketi ekleme

Visual Studio eksik bir NuGet paketi algılarsa, bir ampul belirir ve paketi yüklemenize yönelik bir seçenek sunar:

::: moniker range="<=vs-2019"
![NuGet paketi yüklemeye yönelik ampul ekran görüntüsü.](media/lightbulb-add-package.png)
::: moniker-end
::: moniker range=">=vs-2022"
:::image type="content" source="media/vs-2022/lightbulb-add-package.png" alt-text="NuGet paketi yüklemeye yönelik ampul ekran görüntüsü." border="false":::
::: moniker-end

bu sorunu çözmezse veya Visual Studio paketi bulamıyorsa, paketi çevrimiçi aramayı deneyin. bkz. [Visual Studio NuGet paketini yükleyip kullanma](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

### <a name="use-the-right-version-of-net"></a>.NET sürümünün doğru sürümünü kullanın

.NET Framework farklı sürümlerinin geriye dönük bir uyumluluğu olduğundan, daha yeni bir çerçeve herhangi bir değişiklik yapılmadan eski bir çerçeve için yazılmış kodu çalıştırabilir. Ancak bazen belirli bir .NET Framework sürümünü hedefleyebilirsiniz. .NET Framework veya .net Core 'un belirli bir sürümünü yüklemeniz gerekebilir. Bkz. [Visual Studio değiştirme](../../install/modify-visual-studio.md).

Hedef .NET Framework sürümünü değiştirmek için bkz. [hedef Framework 'Ü değiştirme](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). daha fazla bilgi için bkz. [.NET Framework hedefleme hatalarını giderme](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Sonraki adımlar

- [Visual Studio ıde 'ye hoş geldiniz](../visual-studio-ide.md)'i okuyarak Visual Studio geliştirme ortamını keşfedebilirsiniz.
- [İlk C# uygulamanızı oluşturun.](tutorial-console.md)
