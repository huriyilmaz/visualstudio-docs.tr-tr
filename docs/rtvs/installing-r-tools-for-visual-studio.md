---
title: R araçlarını yükleme
description: Visual Studio 2017 ve Visual Studio 2015 ' de çevrimdışı yüklemeler dahil olmak üzere R araçları 'nı yükleme.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
monikerRange: vs-2017
ms.openlocfilehash: fa5346d65a94646a0fa5e922f3b0055d8cdb6c0d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908658"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Visual Studio için R Araçları nasıl yüklenir

Bu makalede:

- [Desteklenen Visual Studio sürümleri](#supported-versions-of-visual-studio)
- [Visual Studio 2017 ' de RTVS 'yi yükler](#install-rtvs-in-visual-studio-2017)
- [Visual Studio 2015 ' de RTVS 'yi yükler](#install-rtvs-in-visual-studio-2015)
- [Çevrimdışı yükleme](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> R araçları 'nı yükledikten sonra, [Seçenekler](options-for-r-tools-in-visual-studio.md) makalesinde açıklandığı gibi, iyileştirilmiş bir veri bilimi düzeni Için Visual Studio 'yu yapılandırmak isteyebilirsiniz.

## <a name="supported-versions-of-visual-studio"></a>Desteklenen Visual Studio sürümleri

Visual Studio için R Araçları (RTVS), hem [Visual studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) hem de [Visual Studio 2015 güncelleştirme 3 (veya üzeri)](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) (doğrudan indirme) Community (ücretsiz), Professional ve Enterprise sürümleri ile Windows 'da desteklenir.

RTVS, Mac için Visual Studio üzerinde şu anda desteklenmiyor.

Yalnızca Visual Studio Test Professional ve SQL Server Management Studio gibi ürünlerle birlikte bulunan Visual Studio Kabuğu varsa RTVS yüklenmez. Visual Studio Kabuğu, RTVS için gereken bileşenleri eksik.

## <a name="install-rtvs-in-visual-studio-2017"></a>Visual Studio 2017 ' de RTVS 'yi yükler

1. Visual Studio yükleyicisi 'ni çalıştırın ve **Değiştir** seçeneğini belirleyin (Ayrıntılar için bkz. [Visual Studio 'yu değiştirme](../install/modify-visual-studio.md)). Henüz Visual Studio yüklü değilse bkz. [Visual Studio 'Yu yükleme](../install/install-visual-studio.md). Windows 7 ' de, yükleyicinizin Visual Studio 2017 sürüm *15,2 derleme 26430,12* veya üstünü gösterecek şekilde güncelleştirildiğinden emin olun.

1. **Veri bilimi ve analitik uygulamalar** iş yükünü seçin:

    ![VS2017 'de veri bilimi ve analitik uygulamalar iş yükü](media/installation-data-science-workload.png)

1. Aynı iş yükü adının altında, sağ taraftaki ek seçenekleri ayarlayın. Varsayılan olarak, bu iş yükü F # ve Python desteği içerir. R için en düşük gereksinimler **r dil desteği**, **r geliştirme için çalışma zamanı desteği** ve **Microsoft R istemcisi**.

RTVS, ' de yüklü: *% ProgramFiles (x86)% \ Microsoft Visual Studio \<version> \<edition> Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio* , *\<version>* genellikle ve,, `2017` *\<edition>* `Community` `Professional` veya `Enterprise` .

## <a name="install-rtvs-in-visual-studio-2015"></a>Visual Studio 2015 ' de RTVS 'yi yükler

Visual Studio 2015 ile r yorumlayıcı ve R araçlarını ayrı olarak yüklemeniz gerekir.

### <a name="install-an-r-interpreter"></a>R yorumlayıcısı yüklemesi

RTVS, aşağıdaki kaynaklardan biri veya daha fazlası için 64 bitlik bir R sürümü 3.2.1 veya üzeri yüklemesi gerektirir:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open ve CRAN R birden çok yan yana sürüme izin verir. Ancak Microsoft R Client, yalnızca bir sürümü destekler ve her zaman yüklediğiniz en son olanı kullanır.

### <a name="install-the-r-tools"></a>R araçları 'nı yükler

Visual Studio 2015 için geçerli RTVS 'yi indirin [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe) . RTVS, Visual Studio 'nun uygun bir sürümünü denetler ve henüz yapmadıysanız bir R yorumlayıcısı yüklemenize yardımcı olur.

> [!Note]
> Tek başına RTVS yükleyicisi yalnızca Visual Studio 2015 ile kullanılabilir; Visual Studio 2017 ile, daha önce açıklandığı gibi [veri bilimi ve analitik uygulamalar iş yükü](#install-rtvs-in-visual-studio-2017) aracılığıyla R desteği ' ni yükler.

Visual Studio 2015 için RTVS, içine yüklendi: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Visual Studio ve RTVS 'nin çevrimdışı yüklemesi

Çevrimdışı yükleme, Internet 'e bağlı olmayan bilgisayarlar için uygundur:

1. [Çevrimdışı Visual Studio 2017 yüklemesi oluşturun](../install/create-an-offline-installation-of-visual-studio.md)bölümüne gidin.

1. Visual Studio 2015 kullanıyorsanız, içindekiler tablosunun üzerindeki seçicideki **2015** ' yi seçin.

1. Web sayfasında çevrimdışı yükleme oluşturmak için yönergeleri izleyin.

1. Visual Studio 2015 için, ve ' den çevrimdışı RTVS yükleyicilerini indirin [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip) [https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip) .

1. Çevrimdışı yükleyicilerden Visual Studio ve RTVS 'yi yükleme.

## <a name="see-also"></a>Ayrıca bkz.

- [R’yi kullanmaya başlama](getting-started-with-r.md)
- [R araçları örnek projeleri](getting-started-samples.md)
- [R araçlarında yardım](getting-started-help.md)
- [R Araçları seçenekleri](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (eski adıyla R Server)](/machine-learning-server/)
