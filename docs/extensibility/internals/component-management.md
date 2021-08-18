---
title: Bileşen Yönetimi | Microsoft Docs
description: Windows'de VSPackage yükleyicisi oluştururken Windows Yükleyicisi bileşenlerini yönetmeyi Visual Studio.
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
ms.openlocfilehash: 81dcb95e6661cabc75dc55b5a88066362e45f44f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050110"
---
# <a name="component-management"></a>Bileşen yönetimi
Windows Installer'daki görev birimleri, Windows Yükleyici bileşenleri (bazen WIC'ler veya yalnızca bileşenler olarak adlandırılır) olarak adlandırılır. GUID, her WIC'i tanımlar. Bu, yükleyiciyi kullanan kurulumlar için temel yükleme ve başvuru Windows birimidir.

 VSPackage yükleyicinizi oluşturmak için çeşitli ürünler kullanabilirsiniz, ancak bu tartışmada Windows Yükleyicisi (.msi) dosyalarının *kullanımı* varsayılıyor. Yükleyicinizi oluştururken, her zaman doğru başvuru sayma işlemi olması için dosya dağıtımını doğru yönetmeniz gerekir. Sonuç olarak, ürününüz farklı sürümleri yükleme ve kaldırma senaryolarının bir karışımında birbirini engellemez veya bozmaz.

 Bu Windows, başvuru sayma bileşen düzeyinde gerçekleşir. Kaynaklarınızı (dosyalar, kayıt defteri girişleri ve diğer) bileşenlerde dikkatli bir şekilde düzenlemeniz gerekir. Farklı senaryolarda yardımcı olacak başka kuruluş düzeyleri (modüller, özellikler ve ürünler gibi) vardır. Daha fazla bilgi için [bkz. Windows yükleyicisi ile ilgili temel bilgiler.](../../extensibility/internals/windows-installer-basics.md)

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Yan yana yükleme için yazma kurulumu yönergeleri

- Sürümler arasında paylaşılan dosyaları ve kayıt defteri anahtarlarını kendi bileşenlerine yazma.

     Bunu yapmak, bunları bir sonraki sürümde kolayca tüketmenizi sağlar. Örneğin, genel olarak kaydedilen kitaplıkları, dosya uzantılarını, **HKEY_CLASSES_ROOT'a** kaydedilen diğer öğeleri yazın.

- Paylaşılan bileşenleri ayrı birleştirme modülleri halinde grupla.

     Bu strateji, yan yana yüklemenin ilerlemesi için doğru yazmanıza yardımcı olur.

- Paylaşılan dosyaları ve kayıt defteri anahtarlarını, sürümler arasında aynı Windows Yükleyicisi bileşenlerini kullanarak yükleyin.

     Farklı bir bileşen kullanırsanız, sürüme sahip bir VSPackage kaldırılmış ancak başka bir VSPackage hala yüklü olduğunda dosyalar ve kayıt defteri girdileri kaldırılır.

- Sürüme sahip ve paylaşılan öğeleri aynı bileşende karıştırmayın.

     Bunu yapmak, paylaşılan öğelerin genel bir konuma ve sürüme sahip öğelerin yalıtılmış konumlara yüklenmelerini imkansız hale gelir.

- Sürüme sahip dosyalara işaret eder paylaşılan kayıt defteri anahtarlarınız yok.

     Bunu yaparsanız, başka bir sürüme sahip VSPackage yüklü olduğunda paylaşılan anahtarların üzerine yazılır. İkinci sürümü kaldırdikten sonra, anahtarın işarette olduğu dosya yok olur.

## <a name="see-also"></a>Ayrıca bkz.
- [Paylaşılan ve sürüme sahip VSPackage'lar arasında seçim](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage kurulum senaryoları](../../extensibility/internals/vspackage-setup-scenarios.md)
