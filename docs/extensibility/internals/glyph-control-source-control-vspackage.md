---
title: Glyph Control (Kaynak Denetimi VSPackage) | Microsoft Docs
description: Kaynak denetimi altındaki öğelerin durumunu belirtmek için kendi simgelerinizi kullanmak üzere bir kaynak denetimi VSPackage'da özel simgeler görüntülemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8a692473176843730f8cb9c1acfeb90ed164e4ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124600"
---
# <a name="glyph-control-source-control-vspackage"></a>Glyph denetimi (kaynak denetimi VSPackage)
VSPackage'lar kaynak denetimi için kullanılabilen derin tümleştirmenin bir parçası, kaynak denetimi altındaki öğelerin durumunu göstermek için kendi glyph'lerini görüntüleme özelliğidir.

## <a name="levels-of-glyph-control"></a>Glyph denetimi düzeyleri
 Durum işareti, bir öğenin geçerli durumunu (örneğin, öğesinde veya öğesinde) **Çözüm Gezgini** gösteren bir **Sınıf Görünümü.** Bir kaynak denetimi VSPackage iki düzeyde glyph denetimi alıştırması olabilir. Glyph seçimi, IDE tarafından sağlanan önceden tanımlanmış bir dizi glyph ile sınırlayıcı olabilir veya görüntülenecek özel bir dizi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] glyph tanımlayabilir.

### <a name="default-set-of-glyphs"></a>Varsayılan glyph kümesi
 projesinde bir öğeyle ilişkili durum Çözüm Gezgini **belirlemek** için, bir proje kullanarak kaynak denetiminden durum glyph'i talep <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> ediyor. Kaynak denetimi VSPackage, IDE tarafından sağlanan önceden tanımlanmış glyph'ler ile sınırlı olan bir glyph seçimi tutmaya karar verir. Bu durumda VSPackage, *vsshell.idl* içinde tanımlanan glyph sabit değerlerini temsil eden bir değer dizisini geri iletir. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Bu, IDE tarafından ayarlanmış önceden tanımlanmış bir karakter kümesidir( örneğin, iadeli karakter için asma kilit ve kullanıma alınmış karakter için onay işareti).

### <a name="custom-set-of-glyphs"></a>Özel bir dizi glyph
 Kaynak denetimi VSPackage, yüklendikten sonra benzersiz bir görünüm ve his için kendi ifadelerini kullanabilir. VSPackage yeni bir kaynak denetimi etkin olduğunda, önceki bir kaynak denetimi VSPackage hala yüklü ancak devre dışı olsa bile kendi glyph'lerini kullanmaya başlamalıdır. Bu modda, VSPackage kaynak denetimi, seçerse tutarlı bir görünüm elde etmek için mevcut [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] simgeleri kullanmaya devam ediyor.

 Hizmet, <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> VSPackage'ın isteğe bağlı olarak uygulayan ve IDE tarafından istenecek <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> arabirimini destekler. IDE bir istekte olduğunda, bu arabirimi o anda kayıtlı olan kaynak denetimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'dan almaya dener. Arabirim kayıtlı VSPackage içinde mevcutsa, IDE'nin özel glyph'lere olan isteği başarılı olur; aksi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] takdirde, IDE varsayılan glyphs kümelerini kullanır.

 yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> tarafından çeşitli kaynak denetim durumları gösteren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] görüntülerin listesini almak için kullanılır. VSPackage kaynak denetimi, IDE'ye özel özellikleri için görüntü listesinin tanıtıcısını döndürür. IDE, bu noktada görüntü listesinin bir kopyasını yapar ve daha sonra görüntüde yer alan görselleri seçmek için bunu kullanır. Yeni arabirim desteklenmiyorsa veya yöntemi döndürürse, IDE tarafından sağlanan varsayılan `IVsSccGlyphs::GetCustomGlyphList` `E_NOTIMPL` glyph listesinden kendi glyph'lerini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] alır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
