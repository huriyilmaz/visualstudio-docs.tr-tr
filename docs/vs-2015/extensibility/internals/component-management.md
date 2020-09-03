---
title: Bileşen yönetimi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 56a110f382d0b182eed0ea1a95cd4dabf2877037
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191860"
---
# <a name="component-management"></a>Bileşen Yönetimi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Windows Installer görev birimleri Windows Installer bileşenleri (bazen WICs veya yalnızca bileşenler olarak adlandırılır) olarak adlandırılır. Bir GUID, Windows Installer kullanan kurulumlara yönelik temel yükleme birimi ve başvuru sayımı olan her bir WIC 'yi tanımlar.  
  
 VSPackage yükleyicinizi oluşturmak için birkaç ürün kullanabilseniz de, bu tartışma Windows Installer (. msi) dosyalarının kullanımını varsayar. Yükleyicinizi oluştururken doğru başvuru sayımı her zaman gerçekleşmeleri için dosya dağıtımını doğru şekilde yönetmeniz gerekir. Sonuç olarak, ürününüzün farklı sürümleri, yükleme ve kaldırma senaryolarında bir karışımında birbirini engellemez veya bunları bozmaz.  
  
 Windows Installer, bileşen düzeyinde başvuru sayımı oluşur. Kaynaklarınızı (dosyalar, kayıt defteri girişleri vb.) bileşenlere dikkatle düzenlemeniz gerekir. Farklı senaryolarda yardımcı olabilecek modüller, Özellikler ve ürünler gibi diğer kuruluş düzeyleri vardır. Daha fazla bilgi için bkz. [Windows Installer temel kavramları](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Yan yana yükleme için kurulum yazma yönergeleri  
  
- Sürümler arasında paylaşılan dosyaları ve kayıt defteri anahtarlarını kendi bileşenlerine yazar.  
  
     Bu, bunları bir sonraki sürümde kolayca kullanmanıza olanak sağlar. Örneğin, genel olarak kayıtlı kitaplıklar, dosya uzantıları, HKEY_CLASSES_ROOT kayıtlı diğer öğeler ve benzeri.  
  
- Paylaşılan bileşenleri ayrı birleştirme modülleriyle gruplandırın.  
  
     Bu, yan yana taşımaya doğru şekilde yazmanıza yardımcı olur.  
  
- Sürümler arasında aynı Windows Installer bileşenlerini kullanarak paylaşılan dosyaları ve kayıt defteri anahtarlarını yükler.  
  
     Farklı bir bileşen kullanıyorsanız, bir sürümlü VSPackage kaldırıldığında dosya ve kayıt defteri girdileri kaldırılır, ancak başka bir VSPackage hala yüklüdür.  
  
- Aynı bileşendeki sürümlenmiş ve paylaşılan öğeleri karışmayın.  
  
     Bunun yapılması, paylaşılan öğeleri küresel bir konuma ve sürümü tutulan öğeleri yalıtılmış konumlara yüklemeyi olanaksız hale getirir.  
  
- Sürümlü dosyaları işaret eden paylaşılan kayıt defteri anahtarları yok.  
  
     Bunu yaparsanız, başka bir sürümlenmiş VSPackage yüklendiğinde paylaşılan anahtarların üzerine yazılır. İkinci sürümü kaldırdıktan sonra, anahtarın işaret ettiği dosya kayboldu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paylaşılan ve sürümlü VSPackages arasında seçim yapma](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage Kurulum Senaryoları](../../extensibility/internals/vspackage-setup-scenarios.md)
