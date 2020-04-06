---
title: Bileşen Yönetimi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5dcac9fb14a83021b852be2c52436fcdca84bf5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709330"
---
# <a name="component-management"></a>Bileşen yönetimi
Windows Yükleyici'deki görev birimleri Windows Installer bileşenleri (bazen WIC'ler veya yalnızca bileşenler olarak adlandırılır) olarak adlandırılır. GUID, Windows Installer kullanan kurulumlar için temel yükleme ve başvuru sayımı birimi olan her WIC'yi tanımlar.

 VSPackage yükleyicinizi oluşturmak için birkaç ürün kullanabiliyor sanız da, bu tartışma Windows Installer (*.msi*) dosyalarının kullanımını varsayar. Yükleyicinizi oluştururken, doğru başvuru sayımının her zaman gerçekleşmesi için dosya dağıtımını doğru şekilde yönetmeniz gerekir. Sonuç olarak, ürününüzün farklı sürümleri yükleme ve kaldırma senaryolarının bir karışımında birbirini engellemez veya kırılmaz.

 Windows Installer'da, başvuru sayımı bileşen düzeyinde gerçekleşir. Kaynaklarınızı (dosyalar, kayıt defteri girişleri ve benzeri) bileşenler halinde dikkatlice düzenlemeniz gerekir. Modüller, özellikler ve ürünler gibi farklı senaryolarda yardımcı olabilecek başka organizasyon düzeyleri de vardır. Daha fazla bilgi için [Windows Installer temellerine](../../extensibility/internals/windows-installer-basics.md)bakın.

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Yan yana yükleme için kurulum yazma yönergeleri

- Sürümler arasında kendi bileşenlerinde paylaşılan yazar dosyaları ve kayıt defteri anahtarları.

     Bunu yapmak, bunları bir sonraki sürümde kolayca tüketmenizi sağlar. Örneğin, genel olarak kayıtlı kitaplıklar, dosya uzantıları, **HKEY_CLASSES_ROOT**kayıtlı diğer öğeler ve benzeri tür.

- Paylaşılan bileşenleri ayrı birleştirme modüllerinde gruplandırma.

     Bu strateji, yan yana yüklemenin ilerlemesi için doğru şekilde yazmanıza yardımcı olur.

- Sürümler arasında aynı Windows Installer bileşenlerini kullanarak paylaşılan dosyaları ve kayıt defteri anahtarlarını yükleyin.

     Farklı bir bileşen kullanıyorsanız, sürülen vspackage kaldırıldığında ancak başka bir VSPackage hala yüklendiğinde dosyalar ve kayıt defteri girişleri kaldırılır.

- Sürümlenmiş ve paylaşılan öğeleri aynı bileşende karıştırmayın.

     Bunu yapmak, paylaşılan öğeleri genel bir konuma ve sürümlenmiş öğeleri yalıtılmış konumlara yüklemeyi imkansız hale getirir.

- Sürümlenmiş dosyaları gösteren paylaşılan kayıt defteri anahtarları yok.

     Bunu yaparsanız, başka bir sürümlenmiş VSPackage yüklendiğinde paylaşılan anahtarlar üzerine yazılır. İkinci sürümü kaldırdıktan sonra, anahtarın işaret ettiği dosya gider.

## <a name="see-also"></a>Ayrıca bkz.
- [Paylaşılan ve sürümlenmiş VSPackages arasında seçim yapın](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage kurulum senaryoları](../../extensibility/internals/vspackage-setup-scenarios.md)
