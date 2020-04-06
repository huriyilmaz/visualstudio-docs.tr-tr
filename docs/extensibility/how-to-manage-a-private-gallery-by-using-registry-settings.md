---
title: 'Nasıl Yapılır: Kayıt Defteri Ayarlarını Kullanarak Özel Galeri Yi Yönetme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2630fc71bea40a4d05e616ae336759ba62431a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710929"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Nasıl yapılır: Kayıt defteri ayarlarını kullanarak özel bir galeriyi yönetme
Bir yönetici veya Yalıtılmış Kabuk uzantısı geliştiricisiyseniz, Visual Studio Galerisi, Örnekler Galerisi veya özel galerilerde denetimlere, şablonlara ve araçlara erişimi denetleyebilirsiniz. Bir galeriyi kullanılabilir veya kullanılamaz hale getirmek için, değiştirilmiş kayıt defteri anahtarlarını ve değerlerini açıklayan bir *.pkgdef* dosyası oluşturun.

## <a name="manage-private-galleries"></a>Özel galerileri yönetme
 Birden çok bilgisayardaki galerilere erişimi denetlemek için *bir .pkgdef* dosyası oluşturabilirsiniz. Bu dosya aşağıdaki biçime sahip olmalıdır.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Anahtar, `Repositories` etkinleştirilecek veya devre dışı edilecek galeriyi ifade eder. Visual Studio Galerisi ve Örnekler Galerisi aşağıdaki depo GUID'leri kullanır:

- Görsel Stüdyo Galeri : 0F45E408-7995-4375-9485-86B8DB553DC9

- Örnekler Galerisi : AEB9CB40-D8E6-4615-B52C-27E307F8506C

  Değer `Disabled` isteğe bağlıdır. Varsayılan olarak, bir galeri etkinleştirilir.

  Değer, `Priority` galerilerin **Seçenekler** iletişim kutusunda listelenme sırasını belirler. Visual Studio Gallery'nin önceliği 10, Numune Galerisi'nin ise 20 önceliğe sahiptir. Özel galeriler öncelikli 100'den başlar. Birden çok galeri aynı öncelik değerine sahipse, göründükleri sıra yerelleştirilmiş `DisplayName` özniteliklerinin değerleri tarafından belirlenir.

  Değer `Protocol` Atom tabanlı veya SharePoint tabanlı galeriler için gereklidir.

  Ya `DisplayName`, `DisplayNameResourceID` veya `DisplayNamePackageGuid`her ikisi ve , belirtilmelidir. Tüm belirtilirse, `DisplayNameResourceID` o `DisplayNamePackageGuid` zaman ve çifti kullanılır.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>.pkgdef dosyası kullanarak Visual Studio Galerisini devre dışı
 *Bir .pkgdef* dosyasındaki bir galeriyi devre dışı kullanabilirsiniz. Aşağıdaki giriş Visual Studio Galerisi'ni devre dışı kılabilir:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Aşağıdaki giriş Örnekler Galerisi'ni devre dışı kılabilir:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Ayrıca bkz.
- [Özel galeriler](../extensibility/private-galleries.md)
