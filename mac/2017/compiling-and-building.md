---
title: Derleme ve Oluşturma
description: bu makalede Mac için Visual Studio ' de projelerin ve çözümlerin nasıl derlenmesi ve oluşturulacağı açıklanmaktadır
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
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Mac için Visual Studio derleme ve oluşturma

Mac için Visual Studio, projenizin geliştirilmesi sırasında uygulama derlemek ve derlemeler oluşturmak için kullanılabilir. Tür uyuşmazlıklarını ve diğer derleme zamanı hatalarını belirleyebilmeniz için kodunuzun erken ve sık derlenmesi ve oluşturulması önemlidir.

## <a name="building-from-the-ide"></a>IDE 'den oluşturma

Mac için Visual Studio kullanmak, derleme işlevselliği üzerinde size denetim sağlarken yapıları anında oluşturup çalıştırmanıza olanak sağlar. Mac için Visual Studio, temel yapı sistemi olarak MSBuild kullanır.

IDE 'de oluşturulan tüm projeler ve çözümler, derlemelerin bağlamını tanımlayan bir varsayılan derleme yapılandırmasına sahip olacaktır. Bu konfigürasyonlar düzenlenebilir veya kendi kendinize de oluşturabilirsiniz. bu yapılandırmaların oluşturulması veya değiştirilmesi proje dosyasını otomatik olarak güncelleştirir ve bu, daha sonra MSBuild tarafından projenizi oluşturmak için kullanılır.

IDE 'de projeler ve çözümler oluşturma hakkında daha fazla bilgi için, [projeleri ve çözümleri oluşturma ve Temizleme](building-and-cleaning-projects-and-solutions.md) Kılavuzu ' na bakın.

Mac için Visual Studio, aşağıdakileri yapmak için de kullanılabilir:

* Çıkış yolunu değiştirin. bu, Project seçeneklerinde düzenlenmiştir:

    ![Çıkış yolunu değiştir](media/compiling-and-building-image4.png)

* Yapı çıkışının ayrıntı düzeyini değiştirin:

    ![Yapı ayrıntı düzeyini Değiştir](media/compiling-and-building-image5.png)

* Oluşturmadan veya temizlemeden önce, sırasında veya sonrasında özel komutlar ekleyin:

    ![özel komutlar ekleme](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Komut satırından oluşturma

komut satırı aracılığıyla uygulama derlemek için MSBuild yapı altyapısını kullanabilirsiniz.

MSBuild kullanma hakkında daha fazla bilgi için [MSBuild](/visualstudio/msbuild/msbuild) içeriğine bakın.

## <a name="building-from-azure-pipelines"></a>Azure Pipelines oluşturma

* [Xamarin uygulamanızı derleme](/vsts/pipelines/apps/mobile/xamarin?view=vsts&preserve-view=true&tabs=vsts)
* [Xamarin ile sürekli tümleştirme](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>Ayrıca bkz.

- [derle ve derle (Windows üzerinde Visual Studio)](/visualstudio/ide/compiling-and-building-in-visual-studio)