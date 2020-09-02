---
title: Derleme ve Oluşturma
description: Bu makalede Mac için Visual Studio ' de projelerin ve çözümlerin nasıl derlenmesi ve oluşturulacağı açıklanmaktadır
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/29/2019
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: b4f1cfc3dfdffcc3dd4cb90cd7d29d4333578b9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71128414"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Mac için Visual Studio derleme ve oluşturma

Mac için Visual Studio, projenizin geliştirilmesi sırasında uygulama derlemek ve derlemeler oluşturmak için kullanılabilir. Tür uyuşmazlıklarını, hatalı sözdizimini, yanlış yazılmış anahtar sözcükleri ve diğer derleme zamanı hatalarını hızlıca tanımlamanızı sağlamak için kodunuzun oluşturulması önemlidir. Daha sonra hata ayıklamayla, Logic, GÇ ve sıfıra bölme hataları gibi çalışma zamanı hatalarını da bulabilir ve giderebilirsiniz.

Başarılı bir derleme, kaynak kodun doğru sözdizimi içerdiği ve kitaplıklara, derlemelere ve diğer bileşenlere yapılan tüm statik başvuruların çözebileceği anlamına gelir. Yapı işlemi bir uygulama yürütülebilir dosyası üretir. Bu yürütülebilir daha sonra kod kalitesini doğrulamak için hata ayıklama ve farklı türlerde manuel ve otomatikleştirilmiş testler aracılığıyla test edilebilir. Uygulamanız tam olarak sınandıktan sonra, müşterilerinize dağıtmak üzere bir yayın sürümü derleyebilirsiniz.

Mac 'te uygulamanızı derlemek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz: Mac için Visual Studio, MSBuild komut satırı araçları veya Azure Pipelines.

| Build yöntemi | Yararları |
| --- |--- | --- |
| Mac için Visual Studio |-Derlemeleri hemen oluşturun ve bir hata ayıklayıcıda test edin.<br />-C# projeleri için çok işlemcili derlemeler çalıştırın.<br />-Derleme sisteminin farklı yönlerini özelleştirin. |
| MSBuild komut satırı| -Mac için Visual Studio yüklemeden projeler oluşturun.<br />-Tüm proje türleri için çok işlemcili derlemeler çalıştırın.<br />-Yapı sisteminin birçok alanını özelleştirin.|
| Azure Pipelines | -Derleme işleminizi sürekli tümleştirme/sürekli teslim işlem hattının parçası olarak otomatikleştirin.<br />-Her derleme ile otomatikleştirilmiş testler uygulayın.<br />-Derleme işlemlerinde neredeyse sınırsız sayıda bulut tabanlı kaynak kullanmayı.<br />-Derin özelleştirilmiş görevler gerçekleştirmek için derleme iş akışını değiştirin ve derleme etkinlikleri oluşturun.|

Bu bölümdeki belgeler, IDE tabanlı derleme sürecinin daha ayrıntılı ayrıntılarına gider. Komut satırı aracılığıyla uygulama oluşturma hakkında daha fazla bilgi için bkz. [MSBuild](/visualstudio/msbuild/msbuild). Azure Pipelines ile uygulama oluşturma hakkında ayrıntılı bilgi için bkz. [Azure Pipelines](/azure/devops/pipelines).


> [!NOTE]
> Bu konu Mac için Visual Studio için geçerlidir. Windows üzerinde Visual Studio için bkz. [Visual Studio 'Da derleme ve derleme](/visualstudio/ide/compiling-and-building-in-visual-studio).


## <a name="building-from-the-ide"></a>IDE 'den oluşturma

Mac için Visual Studio, derleme işlevselliği üzerinde denetim sağlarken, yapıları hemen oluşturup çalıştırmanıza olanak sağlar. Bir proje oluşturduğunuzda, Mac için Visual Studio yapılar için bağlamı ayarlayan varsayılan yapı yapılandırmasını tanımlar. Varsayılan derleme yapılandırmasını düzenleyebilir ve kendinizinkini de oluşturabilirsiniz. Bu yapılandırmaların oluşturulması veya değiştirilmesi proje dosyasını otomatik olarak güncelleştirir ve bu, daha sonra projenizi derlemek için MSBuild tarafından kullanılır.

IDE 'de projeler ve çözümler oluşturma hakkında daha fazla bilgi için, [projeleri ve çözümleri oluşturma ve Temizleme](building-and-cleaning-projects-and-solutions.md) Kılavuzu ' na bakın.

Mac için Visual Studio, aşağıdakileri yapmak için de kullanılabilir:

* Çıkış yolunu değiştirin. Bu, projenizin seçeneklerinde düzenlenmiştir:

    ![Çıkış yolunu değiştir](media/compiling-and-building-image4.png)

* Yapı çıkışının ayrıntı düzeyini değiştirin:

    ![Yapı ayrıntı düzeyini Değiştir](media/compiling-and-building-image5.png)

* Oluşturmadan veya temizlemeden önce, sırasında veya sonrasında özel komutlar ekleyin:

    ![özel komutlar ekleme](media/compiling-and-building-image6.png)


## <a name="see-also"></a>Ayrıca bkz.

- [Derle ve derle (Windows üzerinde Visual Studio)](/visualstudio/ide/compiling-and-building-in-visual-studio)
