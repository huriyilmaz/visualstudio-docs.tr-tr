---
title: Windows Installer paketi yazma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58529dabbb52ceb751c67be24beb1d21285a1de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301132"
---
# <a name="authoring-a-windows-installer-package"></a>Windows Installer Paketi Yazma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Veri sürücüleri Windows Installer modeli. Dosyaları kopyalamak ve kayıt defteri girişlerini yazmak için bir yordamsal betik yazmak yerine, dosya ve kayıt defteri verilerini içeren veritabanı tablolarında satır ve sütun yazarınız.  
  
## <a name="database-entries"></a>Veritabanı girdileri  
 Bir VSPackage yüklemek için, bir Windows Installer paketi aşağıdaki görevleri gerçekleştirmek üzere veritabanı girdileri içermelidir:  
  
- VSPackage 'ın desteklediği [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sürümlerini bulmak için sistemi arayın (AppSearch, CompLocator, RegLocator, DrLocator ve Signature içeren Windows Installer tabloları kullanarak).  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] desteklenen bir sürümü yüklü değilse veya VSPackage 'ın başka bir sistem gereksinimi karşılanmazsa (LaunchCondition tablosu kullanılarak) yüklemeyi iptal edin.  
  
- VSPackage ve bağımlı dosyaları (Dizin, bileşen ve dosya tablolarını kullanarak) yükler.  
  
- Kayıt defterine VSPackage için uygun bilgileri ekleyin (kayıt defteri tablosunu kullanarak).  
  
- **Devenv. exe/Setup** öğesini çağırarak (CustomAction tablosunu kullanarak) [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage 'ı tümleştirin.  
  
  Daha fazla bilgi için bkz. [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Kurulum araçları  
 Çeşitli üçüncü taraf kurulum araçları, Windows Installer paketlerine yönelik bir geliştirme ortamı sağlar. İki ücretsiz araç şunlardır:  
  
- InstallShield Limited Edition  
  
   Visual Studio **Yeni proje** iletişim kutusunu kullanarak, InstallShield 'ın sınırlı bir sürümünü edinebilirsiniz. **Diğer proje türleri** ' ni genişletin ve ardından **Kurulum ve dağıtım '** ı seçin. InstallShield şablonunu seçin.  
  
- Windows Installer XML Araç Takımı  
  
   Araç takımı, XML kaynak dosyalarından paketleri Windows Installer oluşturur. Araç takımı, Microsoft açık kaynaklı bir projem. Kaynak kodunu ve yürütülebilir dosyaları [http://sourceforge.net/projects/wix](https://sourceforge.net/projects/wix/)yükleyebilirsiniz.  
  
  [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]kullanarak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ile tümleştirilen ticari ürünler için bkz. [https://marketplace.visualstudio.com/](https://marketplace.visualstudio.com/).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer ile VSPackage Yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
