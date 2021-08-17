---
title: VSıX paketleri imzalanıyor | Microsoft Docs
description: Uzantı derlemeleri imzalama hakkında bilgi edinin. VSıX yükleyicisi, bir VSıX 'in imzalandığını ve imza hakkında bilgi görüntüler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c8d82d1e4839a4830eb9a2ac0ac49f80f8e80138
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028624"
---
# <a name="signing-vsix-packages"></a>VSIX Paketlerini İmzalama
uzantı derlemelerinin Visual Studio çalıştırılmadan önce imzalanması gerekmez, ancak bunu yapmak iyi bir uygulamadır.

 Uzantınızı güvenli hale getirmek ve kurcalanmadığından emin olmak istiyorsanız VSıX paketine dijital imza ekleyebilirsiniz. Bir VSıX imzalandığı zaman VSıX yükleyicisi, imzalandığını belirten bir ileti ve imzanın kendisi hakkında daha fazla bilgi görüntüler. VSıX içeriği değiştirilmişse ve VSıX yeniden imzalanmamışsa, VSıX yükleyicisi imza geçerli değil olarak gösterilir. Yükleme durdurulmaz, ancak Kullanıcı uyarıladır.

> [!IMPORTANT]
> Visual Studio 2015 ' den başlayarak, SHA256 şifrelemesi dışında bir şey kullanılarak imzalanmış vsıx paketleri geçersiz imzaya sahip olacak şekilde tanımlanır. VSıX yüklemesi engellenmiyor, ancak Kullanıcı uyarılacaktır.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Valtsigntool ile VSıX imzalama
 [Valtsigntool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)'de NuGet.org üzerinde [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) tarafından kullanılabilen bir SHA256 şifreleme imzalama aracı vardır.

#### <a name="to-use-the-vsixsigntool"></a>Valtsigntool kullanmak için

1. VSıX 'i bir projeye ekleyin.

2. Çözüm Gezgini ' de proje düğümüne sağ tıklayın, **ekle &#124; NuGet paketlerini yönet**' i seçin.  NuGet ve NuGet paketleri ekleme hakkında daha fazla bilgi için [NuGet belgelerine](/NuGet) ve [Paket Yöneticisi kullanıcı arabirimi](/NuGet/Tools/Package-Manager-UI) konularına bakın.

3. VisualStudioExtensibility adresinden valtsigntool araması yapın ve NuGet paketini yükledikten sonra.

4. Şimdi de, projenin yerel paketler konumundan Valtsigntool öğesini çalıştırabilirsiniz. İmzalama senaryonuz (VSIXSignTool.exe/?) için araç komut satırı yardımına bakın.

   Örneğin, parola korumalı bir sertifika dosyası ile imzalamak için:

   VSIXSignTool.exe Sign/f \<certfile> /p \<password>\<VSIXfile>

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Uzantıları Gönderme](../extensibility/shipping-visual-studio-extensions.md)
