---
title: Derleme ve Oluşturma
description: Bu makalede, Mac için Visual Studio'de projelerin ve çözümlerin nasıl derlenmiş ve derlenmiş olduğu Mac için Visual Studio
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2021
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: a24c57907afedb4f02068a071d2c9f81eb8962bb
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964765"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Derleme ve derleme Mac için Visual Studio

Mac için Visual Studio, projenizin geliştirilmesi sırasında uygulama oluşturmak ve derlemeler oluşturmak için kullanılabilir. Tür uyumsuzlarını, hatalı söz dizimlerini, yanlış yazılmış anahtar sözcükleri ve diğer derleme zamanı hatalarını hızla tanımlamanıza olanak tanımak için kodunuzu sık sık derlemeniz önemlidir. Daha sonra hata ayıklamayı kullanarak mantık, IO ve sıfıra bölme hataları gibi çalışma zamanı hatalarını bulup düzeltin.

Başarılı bir derleme, kaynak kodun doğru söz dizimi içerdiği ve kitaplıklara, derlemelere ve diğer bileşenlere yapılan tüm statik başvuruların çözümleyene kadar olduğu anlamına gelir. Derleme işlemi bir uygulama yürütülebilir dosyası üretir. Bu yürütülebilir dosya daha sonra kod kalitesini doğrulamak için hata ayıklama ve farklı türlerde el ile ve otomatikleştirilmiş testler aracılığıyla test edilebilir. Uygulamanız tam olarak test edildikten sonra, müşterilerinize dağıtmak için bir sürüm derleyebilirsiniz.

Mac'te, aşağıdaki yöntemlerden birini kullanarak uygulamalarınızı Mac için Visual Studio, MSBuild komut satırı araçları veya Azure Pipelines.

| Derleme Yöntemi | Avantajlar |
| --- |--- | --- |
| Mac için Visual Studio |- Derlemeleri hemen oluşturun ve bir hata ayıklayıcısında test edin.<br />- C# projeleri için çok işlemcili derlemeler çalıştırın.<br />- Derleme sisteminin farklı yönlerini özelleştirin. |
| MSBuild satırı| - Proje derlemelerini yüklemeden Mac için Visual Studio.<br />- Tüm proje türleri için çok işlemcili derlemeler çalıştırın.<br />- Derleme sisteminin çoğu alanlarını özelleştirin.|
| Azure Pipelines | - Sürekli tümleştirme/sürekli teslim işlem hattının bir parçası olarak derleme sürecinizi otomatikleştirin.<br />- Her derlemeyle otomatikleştirilmiş testler uygulama.<br />- Derleme işlemleri için neredeyse sınırsız bulut tabanlı kaynak kullanın.<br />- Derin özelleştirilmiş görevleri gerçekleştirmek için derleme iş akışını değiştirme ve derleme etkinlikleri oluşturma.|

Bu bölümdeki belgeler, IDE tabanlı derleme işleminin diğer ayrıntılarına gider. Uygulama yüklemeden komut satırına uygulama Mac için Visual Studio için en son sürümü [.NET Core SDK.](https://dotnet.microsoft.com/download) Komut satırı aracılığıyla uygulama bina hakkında daha fazla bilgi için bkz. [MSBuild.](/visualstudio/msbuild/msbuild) Azure Pipelines ile uygulama [Azure Pipelines.](/azure/devops/pipelines).


> [!NOTE]
> Bu konu, Mac için Visual Studio. Visual Studio hakkında daha fazla Windows için [bkz.](/visualstudio/ide/compiling-and-building-in-visual-studio)Derleme ve derleme Visual Studio.


## <a name="building-from-the-ide"></a>IDE'den bina

Mac için Visual Studio derlemeleri anında oluşturmanızı ve çalıştırmanızı sağlarken, yine de derleme işlevselliği üzerinde denetim sağlar. Bir proje yapılandırmasını Mac için Visual Studio için bağlamı ayarladığı varsayılan derleme yapılandırmasını tanımlar. Varsayılan derleme yapılandırmalarını düzenleyebilir ve ayrıca kendi yapılandırmalarınızı oluşturabilirsiniz. Bu yapılandırmaların oluşturulması veya değiştirilmesi, proje dosyasını otomatik olarak güncelleştirecek ve bu dosya projenizi MSBuild için kullanılacaktır.

IDE'de proje ve çözüm oluşturma hakkında daha fazla bilgi için Projeleri ve Çözümleri [Oluşturma ve Temizleme kılavuzuna](building-and-cleaning-projects-and-solutions.md) bakın.

Mac için Visual Studio yapmak için de kullanılabilir:

* Çıkış yolunu değiştirme. Bu, Project seçeneklerinde düzenlenmiştir:

    ![Çıkış yolunu değiştirme](media/compiling-and-building-image4.png)

* Derleme çıkışının ayrıntılıliğini değiştirme:

    ![Derleme ayrıntılılığı değiştirme](media/compiling-and-building-image5.png)

* Bina Özel Komutlar önce, sırasında veya sonrasında aşağıdaki eklemeleri ekleyin:

    ![özel komutlar ekleme](media/compiling-and-building-image6.png)


## <a name="see-also"></a>Ayrıca bkz.

- [Derleme ve derleme (Visual Studio üzerinde Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)
