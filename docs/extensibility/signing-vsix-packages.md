---
title: VSIX Paketlerini İmzalama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17179c35496fc19322c5bb951f4d04bc28e5d7bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700083"
---
# <a name="signing-vsix-packages"></a>VSIX Paketlerini İmzalama
Uzatma derlemelerinin Visual Studio'da çalıştırılmadan önce imzalanması gerekmez, ancak bunu yapmak iyi bir uygulamadır.

 Uzantınızın güvenliğini sağlamak ve üzerinde oynanmış olmadığından emin olmak istiyorsanız, VSIX paketine dijital imza ekleyebilirsiniz. Bir VSIX imzalandığında, VSIX yükleyicisi imzalandığına dair bir ileti ve imzanın kendisi hakkında daha fazla bilgi görüntüler. VSIX'nin içeriği değiştirilmişse ve VSIX yeniden imzalanmadıysa, VSIX yükleyiciimzanın geçerli olmadığını gösterir. Yükleme durdurulmuyor, ancak kullanıcı uyarılır.

> [!IMPORTANT]
> Visual Studio 2015'ten itibaren SHA256 şifrelemesi dışında herhangi bir şey kullanılarak imzalanan VSIX paketlerinin geçersiz imzaya sahip olduğu tespit edilecektir. VSIX yüklemesi engellenmez, ancak kullanıcı uyarılır.

## <a name="signing-a-vsix-with-vsixsigntool"></a>VSIXSignTool ile VSIX İmzalama
 [VsixSignTool'da](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool) [VisualStudioExtensibility'den](https://www.nuget.org/profiles/VisualStudioExtensibility) nuget.org bir SHA256 şifreleme imzalama aracı mevcuttur.

#### <a name="to-use-the-vsixsigntool"></a>VSIXSignTool kullanmak için

1. VSIX'nizi bir projeye ekleyin.

2. Solution Explorer'da proje düğümüne sağ tıklayın, **NuGet Paketlerini &#124; Yönet'i**seçin.  NuGet ve NuGet paketleri ekleme hakkında daha fazla bilgi için [NuGet belgeleri](/NuGet) ve [Paket Yöneticisi Kullanıcı Arabirimi](/NuGet/Tools/Package-Manager-UI) konularına bakın.

3. VisualStudioExtensibility'den VSIXSignTool'u arayın ve NuGet paketini yükleyin.

4. Artık VSIXSignTool'u projenin yerel paket konumundan çalıştırabilirsiniz. İmzalama senaryonuz için aracın komut satırına başvurun (VSIXSignTool.exe /?).

   Örneğin parola korumalı sertifika dosyasıyla imzalamak için:

   VSIXSignTool.exe işareti \</f certfile \<> \</p şifre> VSIXfile>

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Uzantıları Gönderme](../extensibility/shipping-visual-studio-extensions.md)
