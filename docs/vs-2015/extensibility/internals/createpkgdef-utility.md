---
title: CreatePkgDef yardımcı programı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 010ee75efd84f016b0eb68fa9f715102026a4678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64782992"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef Yardımcı Programı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio uzantısı için bir. dll dosyasını parametre olarak alır ve. dll ' ye eşlik eden bir. pkgdef dosyası oluşturur. . Pkgdef dosyası, uzantı yüklendiğinde sistem kayıt defterine yazılabilecek tüm bilgileri içerir.  
  
> [!NOTE]
> Visual Studio SDK 'ya dahil edilen proje şablonlarının çoğu, yapı sürecinin bir parçası olarak. pkgdef dosyalarını otomatik olarak oluşturur. Bu belge, paketleri el ile oluşturmak isteyen veya var olan paketleri. pkgdef dağıtımını kullanacak şekilde dönüştürecek şekilde hazırlanmıştır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 /Out =`FileName`  
 Gereklidir. . Pkgdef çıkış dosyasının adını olarak ayarlar `FileName` .  
  
 /codebase  
 İsteğe bağlı. Kod temeli yardımcı programıyla kayıt işlemini zorlar.  
  
 /Assembly  
 Derleme yardımcı programıyla kayıt işlemini zorlar.  
  
 `AssemblyPath`  
 . Pkgdef oluşturmak istediğiniz. dll dosyasının yolu.  
  
## <a name="remarks"></a>Açıklamalar  
 . Pkgdef dosyaları kullanılarak Uzantı dağıtımı, Visual Studio 'nun önceki sürümlerindeki kayıt defteri gereksinimlerinin yerini alır.  
  
 . Pkgdef dosyaları şu konumlardan birinde yüklü olmalıdır:%localappdata%\Microsoft\Visual Studio\14.0\Extensions\ veya%VSInstallDir%\common7\ıde\extensions \\ . Yükleme klasörü%localappdata%\Microsoft\Visual Studio\14.0\Extensions ise \\ , uzantı Visual Studio tarafından tanınacaktır, ancak varsayılan olarak devre dışı bırakılır. Kullanıcı **uzantıları ve güncelleştirmeleri**kullanarak uzantıyı etkinleştirebilir. Yükleme klasörü%VSInstallDir%\common7\ide\extensions ise \\ , uzantı varsayılan olarak etkinleştirilir.  
  
> [!NOTE]
> **Uzantılar ve güncelleştirmeler** Aracı, bir VSIX paketinin parçası olarak yüklenmediği sürece bir uzantıya erişmek için kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CreateExpInstance Yardımcı Programı](../../extensibility/internals/createexpinstance-utility.md)
