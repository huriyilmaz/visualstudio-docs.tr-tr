---
title: Derleme ve Oluşturma
description: Bu makalede, proje ve çözümleri derleme ve derleme Mac için Visual Studio
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.topic: overview
ms.openlocfilehash: 2fed47263740ed1f60997540eb65ce25217bc3a03984890d408a3dfac68de3f5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121439975"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Derleme ve derleme Mac için Visual Studio

Mac için Visual Studio, projenizin geliştirilmesi sırasında uygulama oluşturmak ve derlemeler oluşturmak için kullanılabilir. Tür yanlışlıklarını ve diğer derleme zamanı hatalarını belirleyesiniz için kodunuzu erken ve sık derlemek önemlidir.

## <a name="building-from-the-ide"></a>IDE'den bina

Bu Mac için Visual Studio, derlemeleri anında oluşturmanıza ve çalıştırmaya devam ederken derleme işlevselliği üzerinde denetiminizi sağlar. Mac için Visual Studio, MSBuild derleme sistemi olarak kullanır.

IDE'de oluşturulan tüm Projeler ve Çözümler, derlemelerin bağlamını tanımlayan varsayılan bir derleme yapılandırmasına sahip olur. Bu yapılandırmalar düzenlenebilir veya kendi yapılandırmanızı oluşturabilirsiniz. Bu yapılandırmaların oluşturulması veya değiştirilmesi, proje dosyasını otomatik olarak güncelleştirecek ve bu dosya projenizi MSBuild için kullanılacaktır.

IDE'de proje ve çözüm oluşturma hakkında daha fazla bilgi için Projeleri ve Çözümleri Oluşturma ve Temizleme [kılavuzuna](building-and-cleaning-projects-and-solutions.md) bakın.

Mac için Visual Studio yapmak için de kullanılabilir:

* Çıkış yolunu değiştirme. Bu, Project seçeneklerinde düzenlenmiştir:

    ![Çıkış yolunu değiştirme](media/compiling-and-building-image4.png)

* Derleme çıkışının ayrıntılıliğini değiştirme:

    ![Derlemenin ayrıntılılıklarını değiştirme](media/compiling-and-building-image5.png)

* Bina Özel Komutlar önce, sırasında veya sonrasında aşağıdaki eklemeleri ekleyin:

    ![özel komutlar ekleme](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Komut satırdan bina

Komut satırı MSBuild derlemek için derleme altyapısını kullanabilirsiniz.

Veri [MSBuild](/visualstudio/msbuild/msbuild) hakkında daha fazla bilgi için bkz. MSBuild.

## <a name="building-from-azure-pipelines"></a>Azure Pipelines'den Azure Pipelines

* [Xamarin Uygulamanızı oluşturma](/vsts/pipelines/apps/mobile/xamarin?view=vsts&preserve-view=true&tabs=vsts)
* [Xamarin ile Sürekli Tümleştirme](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme ve derleme (Visual Studio Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)