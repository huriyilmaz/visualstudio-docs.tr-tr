---
title: 'Nasıl yapılır: kayıt defteri ayarlarını kullanarak özel galeri yönetme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a55b7aa486edfd3775b12dca9d143c2e5f280884
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204154"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Nasıl Yapılır: Bir Özel Galeriyi Kayıt Defteri Ayarlarını Kullanarak Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir Yöneticiyseniz veya yalıtılmış bir kabuk uzantısının geliştiricisiyseniz, Visual Studio galerisinde, örnekler galerisinde veya özel galerilerinde denetimlere, şablonlara ve araçlara erişimi kontrol edebilirsiniz. Bir galeriyi kullanılabilir hale getirmek veya devre dışı bırakmak için, değiştirilmiş kayıt defteri anahtarlarını ve bunların değerlerini açıklayan bir. pkgdef dosyası oluşturun.  
  
## <a name="managing-private-galleries"></a>Özel galerileri yönetme  
 Birden çok bilgisayardaki galerilere erişimi denetlemek için. pkgdef dosyası oluşturabilirsiniz. Bu dosya aşağıdaki biçimde olmalıdır.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories`Anahtar etkinleştirilecek veya devre dışı bırakılacak galeriye başvurur. Visual Studio Galerisi ve Örnekler Galerisi aşağıdaki depo GUID 'Lerini kullanır:  
  
- Visual Studio Galerisi: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Örnekler Galerisi: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  `Disabled`Değer isteğe bağlıdır. Varsayılan olarak, bir galeri etkindir.  
  
  `Priority`Değer, galerinin Seçenekler iletişim kutusunda listelenme sırasını belirler. Visual Studio Galerisinde öncelik 10 ve örnekler galerinin önceliği 20 ' dir. Özel galeriler 100 önceliğiyle başlar. Birkaç galerinin aynı öncelik değeri varsa, bunların görünme sırası yerelleştirilmiş özniteliklerinin değerleriyle belirlenir `DisplayName` .  
  
  `Protocol`Atom tabanlı veya SharePoint tabanlı Galeriler için bu değer gereklidir.  
  
  Ya da `DisplayName` her ikisi `DisplayNameResourceID` de `DisplayNamePackageGuid` belirtilmelidir. Tümü belirtilmişse, `DisplayNameResourceID` ve `DisplayNamePackageGuid` çifti kullanılır.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Bir. pkgdef dosyası kullanarak Visual Studio galerisini devre dışı bırakma  
 Bir. pkgdef dosyasındaki bir galeriyi devre dışı bırakabilirsiniz. Aşağıdaki giriş, Visual Studio galerisini devre dışı bırakır:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 Aşağıdaki girdi, örnekler galerisini devre dışı bırakır:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Galeriler](../extensibility/private-galleries.md)
