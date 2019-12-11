---
title: Derleme ve Oluşturma
description: Bu makalede Mac için Visual Studio ' de projelerin ve çözümlerin nasıl derlenmesi ve oluşturulacağı açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: 0165594b4c2d77005c2a9ef921cce457f6f2d0f6
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983610"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Mac için Visual Studio derleme ve oluşturma

Mac için Visual Studio, projenizin geliştirilmesi sırasında uygulama derlemek ve derlemeler oluşturmak için kullanılabilir. Tür uyuşmazlıklarını ve diğer derleme zamanı hatalarını belirleyebilmeniz için kodunuzun erken ve sık derlenmesi ve oluşturulması önemlidir.

## <a name="building-from-the-ide"></a>IDE içinden derleme

Mac için Visual Studio kullanmak, derleme işlevselliği üzerinde size denetim sağlarken yapıları anında oluşturup çalıştırmanıza olanak sağlar. Mac için Visual Studio, temel yapı sistemi olarak MSBuild 'i kullanır.

IDE 'de oluşturulan tüm projeler ve çözümler, derlemelerin bağlamını tanımlayan bir varsayılan derleme yapılandırmasına sahip olacaktır. Bu konfigürasyonlar düzenlenebilir veya kendi kendinize de oluşturabilirsiniz. Bu yapılandırmaların oluşturulması veya değiştirilmesi proje dosyasını otomatik olarak güncelleştirir ve bu, daha sonra projenizi derlemek için MSBuild tarafından kullanılır.

IDE 'de projeler ve çözümler oluşturma hakkında daha fazla bilgi için, [projeleri ve çözümleri oluşturma ve Temizleme](building-and-cleaning-projects-and-solutions.md) Kılavuzu ' na bakın.

Mac için Visual Studio, aşağıdakileri yapmak için de kullanılabilir:

* Çıkış yolunu değiştirin. Bu, projenizin seçeneklerinde düzenlenmiştir:

    ![Çıkış yolunu değiştir](media/compiling-and-building-image4.png)

* Yapı çıkışının ayrıntı düzeyini değiştirin:

    ![Yapı ayrıntı düzeyini Değiştir](media/compiling-and-building-image5.png)

* Oluşturmadan veya temizlemeden önce, sırasında veya sonrasında özel komutlar ekleyin:

    ![özel komutlar ekleme](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Komut satırından oluşturma

MSBuild derleme altyapısını komut satırı aracılığıyla uygulamalar oluşturmak için kullanabilirsiniz.

MSBuild 'i kullanma hakkında daha fazla bilgi için bkz. [MSBuild](/visualstudio/msbuild/msbuild) içeriği.

## <a name="building-from-azure-pipelines"></a>Azure Pipelines oluşturma

* [Xamarin uygulamanızı derleme](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts)
* [Xamarin ile sürekli tümleştirme](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>Ayrıca bkz.

- [Derle ve derle (Windows üzerinde Visual Studio)](/visualstudio/ide/compiling-and-building-in-visual-studio)