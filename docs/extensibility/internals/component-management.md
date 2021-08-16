---
title: Bileşen yönetimi | Microsoft Docs
description: Visual Studio bir vspackage yükleyicisi oluştururken Windows Installer bileşenlerini yönetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6ff094b0ad7457eabc569ce10d44a80c1f6db639cc7c855dc4f27c77c68edbc4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275534"
---
# <a name="component-management"></a>Bileşen yönetimi
Windows Installer görev birimleri Windows Installer bileşenleri (bazen wics veya yalnızca bileşenler olarak adlandırılır) olarak adlandırılır. bir guıd, Windows Installer kullanan kurulumlara yönelik temel yükleme birimi ve başvuru sayımı olan her bir wic 'yi tanımlar.

 vspackage yükleyicinizi oluşturmak için birkaç ürün kullanabilirsiniz, ancak bu tartışma Windows Installer (*.msi*) dosyalarının kullanımını varsayar. Yükleyicinizi oluştururken doğru başvuru sayımı her zaman gerçekleşmeleri için dosya dağıtımını doğru şekilde yönetmeniz gerekir. Sonuç olarak, ürününüzün farklı sürümleri, yükleme ve kaldırma senaryolarında bir karışımında birbirini engellemez veya bunları bozmaz.

 Windows Installer, bileşen düzeyinde başvuru sayımı oluşur. Kaynaklarınızı (dosyalar, kayıt defteri girişleri vb.) bileşenlere dikkatle düzenlemeniz gerekir. Farklı senaryolarda yardımcı olabilecek modüller, Özellikler ve ürünler gibi diğer kuruluş düzeyleri vardır. daha fazla bilgi için bkz. [Windows Installer temel kavramları](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Yan yana yükleme için kurulum yazma yönergeleri

- Sürümler arasında paylaşılan dosyaları ve kayıt defteri anahtarlarını kendi bileşenlerine yazar.

     Bunun yapılması, bunları bir sonraki sürümde kolayca kullanmanıza olanak sağlar. Örneğin, genel olarak kayıtlı kitaplıklar, dosya uzantıları, **HKEY_CLASSES_ROOT** kayıtlı diğer öğeler ve benzeri.

- Paylaşılan bileşenleri ayrı birleştirme modülleriyle gruplandırın.

     Bu strateji, yan yana yükleme sırasında doğru şekilde yazmanıza yardımcı olur.

- sürümler arasında aynı Windows Installer bileşenlerini kullanarak paylaşılan dosyaları ve kayıt defteri anahtarlarını yükler.

     Farklı bir bileşen kullanıyorsanız, bir sürümlü VSPackage kaldırıldığında dosya ve kayıt defteri girdileri kaldırılır, ancak başka bir VSPackage hala yüklüdür.

- Aynı bileşendeki sürümlenmiş ve paylaşılan öğeleri karışmayın.

     Bunun yapılması, paylaşılan öğeleri küresel bir konuma ve sürümü tutulan öğeleri yalıtılmış konumlara yüklemeyi olanaksız hale getirir.

- Sürümlü dosyaları işaret eden paylaşılan kayıt defteri anahtarları yok.

     Bunu yaparsanız, başka bir sürümlenmiş VSPackage yüklendiğinde paylaşılan anahtarların üzerine yazılır. İkinci sürümü kaldırdıktan sonra, anahtarın işaret ettiği dosya kayboldu.

## <a name="see-also"></a>Ayrıca bkz.
- [Paylaşılan ve sürümlenmiş VSPackages arasında seçim yapın](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage kurulum senaryoları](../../extensibility/internals/vspackage-setup-scenarios.md)
