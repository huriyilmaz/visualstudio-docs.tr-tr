---
title: VSıX paketleri imzalanıyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2e97845c7ef17476e18e0068663772341ad8eb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983122"
---
# <a name="signing-vsix-packages"></a>VSIX Paketlerini İmzalama
Uzantı derlemelerinin Visual Studio 'da çalıştırılmadan önce imzalanması gerekmez, ancak bunu yapmak iyi bir uygulamadır.

 Uzantınızı güvenli hale getirmek ve kurcalanmadığından emin olmak istiyorsanız VSıX paketine dijital imza ekleyebilirsiniz. Bir VSıX imzalandığı zaman VSıX yükleyicisi, imzalandığını belirten bir ileti ve imzanın kendisi hakkında daha fazla bilgi görüntüler. VSıX içeriği değiştirilmişse ve VSıX yeniden imzalanmamışsa, VSıX yükleyicisi imza geçerli değil olarak gösterilir. Yükleme durdurulmaz, ancak Kullanıcı uyarıladır.

> [!IMPORTANT]
> Visual Studio 2015 ' den başlayarak, SHA256 şifrelemesi dışında bir şey kullanılarak imzalanmış VSıX paketleri geçersiz imzaya sahip olacak şekilde tanımlanır. VSıX yüklemesi engellenmiyor, ancak Kullanıcı uyarılacaktır.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Valtsigntool ile VSıX imzalama
 [Valtsigntool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)'de NuGet.org üzerinde [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) tarafından kullanılabilen bir SHA256 şifreleme imzalama aracı vardır.

#### <a name="to-use-the-vsixsigntool"></a>Valtsigntool kullanmak için

1. VSıX 'i bir projeye ekleyin.

2. Çözüm Gezgini ' de proje düğümüne sağ tıklayıp **NuGet Paketlerini Yönet Ekle &#124;** ' yi seçin.  NuGet ve NuGet paketleri ekleme hakkında daha fazla bilgi için bkz. [NuGet belge](/NuGet) ve [Paket Yöneticisi Kullanıcı arabirimi](/NuGet/Tools/Package-Manager-UI) konuları.

3. VisualStudioExtensibility adresinden Valtsigntool araması yapın ve NuGet paketini yükledikten sonra.

4. Şimdi de, projenin yerel paketler konumundan Valtsigntool öğesini çalıştırabilirsiniz. İmzalama senaryonuz (Valtsigntool. exe/?) için araç komut satırı yardımına bakın.

   Örneğin, parola korumalı bir sertifika dosyası ile imzalamak için:

   Valtsigntool. exe Sign/f \<certfile >/p \<password > \<VSIXfile >

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Uzantıları Gönderme](../extensibility/shipping-visual-studio-extensions.md)
