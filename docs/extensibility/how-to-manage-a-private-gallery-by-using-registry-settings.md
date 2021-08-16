---
title: Kayıt defteri ayarlarını kullanarak özel galeriyi yönetme
description: Visual Studio Galerisi, Örnekler Galerisi veya özel galerilerde denetimlere, şablonlara ve araçlara erişimi denetlemeyi öğrenin.
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
ms.openlocfilehash: e1048f5af6457d8429694c73f37e82f5b420bc66f08abd198016388441346f40
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414707"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Nasıl yapabilirsiniz: Kayıt defteri ayarlarını kullanarak özel galeriyi yönetme
Yalıtılmış Kabuk uzantısının yöneticisi veya geliştiricisiyseniz, Visual Studio Galerisi, Örnekler Galerisi veya özel galeriler'deki denetimlere, şablonlara ve araçlara erişimi kontrol edin. Bir galeriyi kullanılabilir veya kullanılamaz hale getirirken, değiştirilen kayıt defteri anahtarlarını ve bunların değerlerini açıklayan bir *.pkgdef* dosyası oluşturun.

## <a name="manage-private-galleries"></a>Özel galerileri yönetme
 Birden çok bilgisayarda galerilere erişimi kontrol etmek için *bir .pkgdef* dosyası oluşturabilirsiniz. Bu dosya aşağıdaki biçime sahip olmalıdır.

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

 Anahtar, `Repositories` galerinin etkinleştirilmesi veya devre dışı bırakılacak olması anlamına gelir. Visual Studio Galerisi ve Örnekler Galerisi aşağıdaki depo GUID'lerini kullanır:

- Visual Studio Galeri: 0F45E408-7995-4375-9485-86B8DB553DC9

- Örnek Galerisi: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  Değer `Disabled` isteğe bağlıdır. Varsayılan olarak bir galeri etkindir.

  değer, `Priority` galerilerin Seçenekler iletişim kutusunda listelenmiş olduğu **sırayı** belirler. Visual Studio Galerinin önceliği 10, Örnek Galerisi'nin önceliği 20'dir. Özel galeriler 100 öncelikli olarak başlar. Birden fazla galeri aynı öncelik değerine sahipse, bunların görünme sırası yerelleştirilmiş özniteliklerinin `DisplayName` değerlerine göre belirlenir.

  Bu `Protocol` değer, Atom tabanlı veya SharePoint galeriler için gereklidir.

  , `DisplayName` veya her ikisi ve `DisplayNameResourceID` `DisplayNamePackageGuid` belirtilmelidir. Tüm belirtilirse ve `DisplayNameResourceID` `DisplayNamePackageGuid` çifti kullanılır.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>.pkgdef Visual Studio Galeri'yi devre dışı bırakma
 .pkgdef dosyasındaki bir *galeriyi devre dışı abilirsiniz.* Aşağıdaki giriş, Visual Studio Galerisi'ni devre dışı bıraktır:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Aşağıdaki giriş, Örnek Galerisi'ni devre dışı bıraktır:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Ayrıca bkz.
- [Özel galeriler](../extensibility/private-galleries.md)
