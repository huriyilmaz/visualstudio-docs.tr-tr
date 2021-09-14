---
title: R Araçlarını Yükleme
description: Visual Studio 2017 ve Visual Studio 2015'te çevrimdışı yüklemeler de dahil olmak üzere R Araçlarını yükleme.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
monikerRange: vs-2017
ms.openlocfilehash: 028746c19729395f36ae7035a34d82386f89af72
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625322"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Visual Studio için R Araçları'i yükleme

Bu makalede:

- [Desteklenen Visual Studio sürümleri](#supported-versions-of-visual-studio)
- [Visual Studio 2017'de RTVS yükleme](#install-rtvs-in-visual-studio-2017)
- [Visual Studio 2015'te RTVS yükleme](#install-rtvs-in-visual-studio-2015)
- [Çevrimdışı yükleme](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> R Araçlarını yükledikten sonra Seçenekler makalesinde açıklandığı Visual Studio iyileştirilmiş bir veri bilimcisi düzeni için yapılandırmayı [yapılandırabilirsiniz.](options-for-r-tools-in-visual-studio.md)

## <a name="supported-versions-of-visual-studio"></a>Desteklenen Visual Studio sürümleri

Visual Studio için R Araçları (RTVS), hem Visual Studio [2017](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) hem de Visual Studio [2015](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Güncelleştirme 3(veya daha yenisi) (doğrudan indirme) Community (ücretsiz), Professional ve Enterprise sürümleriyle Windows'de de desteklemektedir.

RTVS şu anda Mac için Visual Studio.

RtVS, yalnızca Visual Studio Test Professional ve SQL Server Management Studio gibi ürünlere dahil olan Visual Studio Shell'i SQL Server Management Studio. Visual Studio Kabukta RTVS için gerekli bileşenler yoktur.

## <a name="install-rtvs-in-visual-studio-2017"></a>Visual Studio 2017'de RTVS yükleme

1. Uygulama yükleyicisini Visual Studio ve Değiştir seçeneğini **belirleyin** (ayrıntılar için [bkz.](../install/modify-visual-studio.md)Visual Studio). Henüz yüklü değil Visual Studio bkz. [Yükleme Visual Studio.](../install/install-visual-studio.md) 7 Windows de, yükleyicinizin *26430.12* veya sonraki Visual Studio 15.2 sürümünü gösterecek şekilde güncelleştirilmiş olduğundan emin olun.

1. Veri bilimi **ve analitik uygulamalar iş yükünü** seçin:

    ![VS2017'de veri bilimi ve analitik uygulamalar iş yükü](media/installation-data-science-workload.png)

1. Sağ tarafta aynı iş yükü adının altında ek seçenekleri ayarlayın. Varsayılan olarak, bu iş yükü F# ve Python desteğini içerir. R için en düşük gereksinimler **R dil desteği, R** geliştirme için çalışma zamanı desteği **ve** Microsoft **R istemcisidir.**

RTVS şu dizinde yüklenir: *%ProgramFiles(x86)%\Microsoft Visual Studio \<version> \<edition> Common7\IDE\Extensions\Microsoft\Visual Studio için R Araçları* burada genellikle ve *\<version>* , veya `2017` *\<edition>* `Community` `Professional` `Enterprise` olur.

## <a name="install-rtvs-in-visual-studio-2015"></a>Visual Studio 2015'te RTVS yükleme

2015'Visual Studio ile bir R yorumlayıcı ve R Araçları ayrı ayrı yüklemeniz gerekir.

### <a name="install-an-r-interpreter"></a>R yorumlayıcı yükleme

RTVS, R sürüm 3.2.1 veya sonraki bir sürümün aşağıdaki kaynaklardan bir veya daha fazla 64 bit yüklemesini gerektirir:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open ve CRAN R birden çok yan yana sürüme olanak sağlar. Microsoft R Client, yalnızca bir sürümü destekler ve her zaman yüklü olan en son sürümü kullanır.

### <a name="install-the-r-tools"></a>R araçlarını yükleme

Visual Studio 2015 için geçerli RTVS'i [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe) indirin. RTVS, daha önce Visual Studio sürümü olup olmadığını denetler ve R yorumlayıcı yüklemenize yardımcı olur.

> [!Note]
> Tek başına RTVS yükleyicisi yalnızca Visual Studio 2015'te çalışır; 2017 Visual Studio de açıklandığı gibi Veri Bilimi ve Analitik Uygulamalar iş yükü [aracılığıyla](#install-rtvs-in-visual-studio-2017) R desteğini yükleyin.

Visual Studio 2015 için RTVS şu işletim sistemiyle yüklenir:`%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Visual Studio ve RTVS'nin çevrimdışı yüklemesi

Çevrimdışı yükleme, İnternet'e bağlı olan bilgisayarlar için uygundur:

1. Visual Studio [2017'nin çevrimdışı yüklemesi oluştur'a gidin.](../install/create-an-offline-installation-of-visual-studio.md)

1. 2015'Visual Studio kullanıyorsanız içindekiler tablosundaki seçicide **2015'i** seçin.

1. Web sayfasında çevrimdışı yükleme oluşturma yönergelerini izleyin.

1. 2015 Visual Studio için ve 'den çevrimdışı RTVS yükleyicilerini [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip) [https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip) indirin.

1. Çevrimdışı Visual Studio ve RTVS'leri yükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [R’yi kullanmaya başlama](getting-started-with-r.md)
- [R Araçları örnek projeleri](getting-started-samples.md)
- [R Araçlarında Yardım](getting-started-help.md)
- [R Araçları seçenekleri](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (eski adı R Server)](/machine-learning-server/)
