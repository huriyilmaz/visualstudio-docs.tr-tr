---
title: R Araçlarının Yüklenmesi
description: Çevrimdışı kurulumlar da dahil olmak üzere Visual Studio 2017 ve Visual Studio 2015'te R Tools nasıl yüklenir?
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
monikerRange: vs-2017
ms.openlocfilehash: 5a09b3f78b929fd60764be36f56c0b580c7a42d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75843736"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Visual Studio için R Araçları nasıl yüklenir?

Bu makalede:

- [Visual Studio'nun desteklenen versiyonları](#supported-versions-of-visual-studio)
- [Visual Studio 2017'de RTVS'yi yükleyin](#install-rtvs-in-visual-studio-2017)
- [Visual Studio 2015'te RTVS'yi yükleyin](#install-rtvs-in-visual-studio-2015)
- [Çevrimdışı yükleme](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> R Tools'u yükledikten sonra, [Seçenekler](options-for-r-tools-in-visual-studio.md) makalesinde açıklandığı gibi Visual Studio'yu optimize edilmiş bir veri bilimci düzeni için yapılandırmak isteyebilirsiniz.

## <a name="supported-versions-of-visual-studio"></a>Visual Studio'nun desteklenen versiyonları

R Tools for Visual Studio (RTVS), [Visual Studio 2017 ve Visual Studio 2015](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) [Update 3 (veya daha yüksek)](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) (doğrudan indir) sürümlerinde Windows with the Community (ücretsiz), Professional ve Enterprise sürümlerinde desteklenir.

RTVS şu anda Visual Studio for Mac'te desteklenmez.

Visual Studio Test Professional ve SQL Server Management Studio gibi ürünlerle birlikte sadece Visual Studio Shell'e sahipseniz RTVS yüklemez. Visual Studio Shell, RTVS için gerekli bileşenlerden yoksundur.

## <a name="install-rtvs-in-visual-studio-2017"></a>Visual Studio 2017'de RTVS'yi yükleyin

1. Visual Studio yükleyicisini çalıştırın ve **Değiştir** seçeneğini seçin (ayrıntılar için [Bkz. Görsel Stüdyoyu Değiştir).](../install/modify-visual-studio.md) Visual Studio'ya henüz yüklemeyapmadıysanız, [Visual Studio'yı yükle'ye](../install/install-visual-studio.md)bakın. Windows 7'de, yükleyicinizin Visual Studio 2017 sürüm *15.2 build 26430.12* veya sonrakilerini gösterecek şekilde güncellendiğinden emin olun.

1. Veri **bilimi ve analitik uygulamalar** iş yükünü seçin:

    ![VS2017'de veri bilimi ve analitik uygulamalar iş yükü](media/installation-data-science-workload.png)

1. Sağ taraftaki ek seçenekleri aynı iş yükü adı altında ayarlayın. Varsayılan olarak, bu iş yükü F# ve Python desteğini içerir. R için minimum gereksinimler **R dil desteği,** **R geliştirme için çalışma zamanı desteği**ve Microsoft R **istemcisidir.**

RTVS yüklü: *%ProgramFiles(x86)%\Microsoft Visual\<Studio \<sürümü>sürümü>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio* nerede `Community` `Professional` `Enterprise` * \<sürüm>* genellikle `2017` ve * \<sürüm>* , , veya .

## <a name="install-rtvs-in-visual-studio-2015"></a>Visual Studio 2015'te RTVS'yi yükleyin

Visual Studio 2015 ile bir R tercümanı ve R Tools'u ayrı ayrı yüklemeniz gerekir.

### <a name="install-an-r-interpreter"></a>R tercümanı yükleme

RTVS, aşağıdaki kaynaklardan biri veya daha fazlası olan R sürüm 3.2.1 veya daha yüksek 64 bit yüklemegerektirir:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R İstemci](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open ve CRAN R'nin her ikisi de birden çok yan yana sürüme izin verir. Ancak Microsoft R İstemci yalnızca bir sürümü destekler ve her zaman yüklediğiniz en son sürümü kullanır.

### <a name="install-the-r-tools"></a>R araçlarını yükleme

Visual Studio 2015 için geçerli RTVS indirin [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe). RTVS Visual Studio'nun uygun bir sürümünü denetler ve henüz yapmadıysanız bir R yorumlayıcısı yüklemenize yardımcı olur.

> [!Note]
> Bağımsız RTVS yükleyici si Görsel Studio 2015 ile çalışır; Visual Studio 2017 ile, daha önce açıklandığı gibi [Veri Bilimi ve Analitik Uygulamalar iş yükü](#install-rtvs-in-visual-studio-2017) aracılığıyla R desteği yükleyin.

Visual Studio 2015 için RTVS şu şekilde yüklenir:`%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Visual Studio ve RTVS'nin çevrimdışı kurulumu

Çevrimdışı yükleme, Internet'e bağlı olmayan bilgisayarlar için uygundur:

1. Visual [Studio 2017'nin çevrimdışı yüklemesini oluşturma 'ya](../install/create-an-offline-installation-of-visual-studio.md)gidin.

1. Visual Studio 2015 kullanıyorsanız, içindekiler tablosunun üstündeki seçicide **2015'i** seçin.

1. Web sayfasında çevrimdışı yükleme oluşturmak için yönergeleri izleyin.

1. Visual Studio 2015 için çevrimdışı RTVS yükleyicilerini indirin [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip) ve [https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip).

1. Çevrimdışı yükleyicilerden Visual Studio ve RTVS'yi yükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [R ile başlayın](getting-started-with-r.md)
- [R Araçları örnek projeler](getting-started-samples.md)
- [R Araçlarında Yardım](getting-started-help.md)
- [R Araçları seçenekleri](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (eski adıyla R Server)](/machine-learning-server/)
