---
title: Kayıt defteri ayarlarını kullanarak özel bir galeri yönetme
description: Visual Studio galerisinde, örnek galerisinde veya özel galerilerinde denetimlere, şablonlara ve araçlara erişimi nasıl denetleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 38cc90f557bb901f2ef9710bc1cd129e471a3781
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124940"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Nasıl yapılır: kayıt defteri ayarlarını kullanarak özel galeri yönetme
bir yönetici veya yalıtılmış bir kabuk uzantısının geliştiricisiyseniz, Visual Studio galerisinde, şablonlara ve araçlara erişimi denetleyebilir, örnekler galerisi veya özel galerilere erişebilirsiniz. Bir galeriyi kullanılabilir hale getirmek veya devre dışı bırakmak için, değiştirilmiş kayıt defteri anahtarlarını ve bunların değerlerini açıklayan bir *. pkgdef* dosyası oluşturun.

## <a name="manage-private-galleries"></a>Özel galerileri yönetme
 Birden çok bilgisayardaki galerilere erişimi denetlemek için *. pkgdef* dosyası oluşturabilirsiniz. Bu dosya aşağıdaki biçimde olmalıdır.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 `Repositories`Anahtar etkinleştirilecek veya devre dışı bırakılacak galeriye başvurur. Visual Studio galerisi ve örnekler galerisi aşağıdaki depo guıd 'lerini kullanır:

- Visual Studio Galeri: 0F45E408-7995-4375-9485-86B8DB553DC9

- Örnekler Galerisi: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  `Disabled`Değer isteğe bağlıdır. Varsayılan olarak, bir galeri etkindir.

  `Priority`Değer, galerinin **Seçenekler** iletişim kutusunda listelenme sırasını belirler. Visual Studio Galeri öncelik 10 ' a sahiptir ve örnekler galerisinde 20 öncelik vardır. Özel galeriler 100 önceliğiyle başlar. Birkaç galerinin aynı öncelik değeri varsa, bunların görünme sırası yerelleştirilmiş özniteliklerinin değerleriyle belirlenir `DisplayName` .

  `Protocol`değer, Atom tabanlı veya SharePoint tabanlı galeriler için gereklidir.

  Ya da `DisplayName` her ikisi `DisplayNameResourceID` de `DisplayNamePackageGuid` belirtilmelidir. Tümü belirtilmişse, `DisplayNameResourceID` ve `DisplayNamePackageGuid` çifti kullanılır.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>bir. pkgdef dosyası kullanarak Visual Studio galerisini devre dışı bırakma
 Bir *. pkgdef* dosyasındaki bir galeriyi devre dışı bırakabilirsiniz. aşağıdaki girdi Visual Studio galerisini devre dışı bırakır:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Aşağıdaki girdi, örnekler galerisini devre dışı bırakır:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Ayrıca bkz.
- [Özel galeriler](../extensibility/private-galleries.md)
