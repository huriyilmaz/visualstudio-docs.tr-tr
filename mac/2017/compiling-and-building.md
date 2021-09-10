---
title: Derleme ve Oluşturma
description: Bu makalede, Mac için Visual Studio'de projelerin ve çözümlerin nasıl derlenmiş ve derlenmiş olduğu Mac için Visual Studio
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.topic: overview
ms.openlocfilehash: d5613a47785f1bb3fbb2a56f8458bba1946930e7
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962113"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Derleme ve derleme Mac için Visual Studio

Mac için Visual Studio, projenizin geliştirilmesi sırasında uygulama oluşturmak ve derlemeler oluşturmak için kullanılabilir. Tür hataları ve diğer derleme zamanı hatalarını belirleyesiniz için kodunuzu erken ve sık derlemek önemlidir.

## <a name="building-from-the-ide"></a>IDE'den bina

Bu Mac için Visual Studio, derlemeleri anında oluşturmanıza ve çalıştırmaya devam ederken derleme işlevselliği üzerinde denetiminizi sağlar. Mac için Visual Studio, MSBuild derleme sistemi olarak kullanır.

IDE'de oluşturulan tüm Projeler ve Çözümler, derlemelerin bağlamını tanımlayan varsayılan bir derleme yapılandırmasına sahip olur. Bu yapılandırmalar düzenlenebilir veya kendi yapılandırmanızı oluşturabilirsiniz. Bu yapılandırmaların oluşturulması veya değiştirilmesi, proje dosyasını otomatik olarak güncelleştirecek ve bu dosya projenizi MSBuild için kullanılacaktır.

IDE'de proje ve çözüm oluşturma hakkında daha fazla bilgi için Projeleri ve Çözümleri [Oluşturma ve Temizleme kılavuzuna](building-and-cleaning-projects-and-solutions.md) bakın.

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

- [Derleme ve derleme (Visual Studio üzerinde Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)