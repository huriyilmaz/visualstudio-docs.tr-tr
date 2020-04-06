---
title: Glyph Kontrolü (Kaynak Kontrol VSPackage) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9db1b4542eae293e39cda674fac3eb984aa77d3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708314"
---
# <a name="glyph-control-source-control-vspackage"></a>Glyph kontrolü (kaynak kontrolü VSPackage)
Kaynak denetimi VSPackages için kullanılabilir derin entegrasyon parçası kaynak denetimi altında öğelerin durumunu belirtmek için kendi glifleri görüntülemek için yeteneğidir.

## <a name="levels-of-glyph-control"></a>Gliflerin kontrol düzeyleri
 Durum glyph'si, örneğin **Çözüm Gezgini'nde** veya **Sınıf Görünümü'nde**görüntülendiğinde öğenin geçerli durumunu gösteren bir simgedir. Bir kaynak kontrolü VSPackage glyph kontrolü iki düzeyde egzersiz yapabilirsiniz. Gliflerin seçimini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tarafından sağlanan önceden tanımlanmış bir glifler kümesiyle sınırlandırabilir veya görüntülenecek özel bir glifler kümesi tanımlayabilir.

### <a name="default-set-of-glyphs"></a>Varsayılan glifler kümesi
 **Çözüm Gezgini'nde**bir öğeyle ilişkili durum glifleri belirlemek için, bir proje kaynak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>denetiminden durum glifleri ister. Bir kaynak kontrolü VSPackage Gliflerin seçimi ide tarafından sağlanan önceden tanımlanmış glifler ile sınırlı tutmaya karar verebilir. Bu durumda, VSPackage *vsshell.idl*tanımlanan glyph sayısallamaları temsil eden bir dizi değer geri verir. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Bu, IDE tarafından ayarlanmış önceden tanımlanmış bir glifler kümesidir, örneğin iade edilmiş glyph için bir asma kilit ve kullanıma alındı glyph için bir onay işareti.

### <a name="custom-set-of-glyphs"></a>Özel glifler seti
 Bir kaynak kontrolü VSPackage, yüklendiğinde benzersiz bir görünüm ve his için kendi glifleri kullanabilirsiniz. Yeni bir kaynak denetimi VSPackage etkin olduğunda, önceki bir kaynak denetimi VSPackage hala yüklü ama etkin olmasa bile kendi glifleri kullanmaya başlamak gerekir. Bu modda, kaynak denetimi VSPackage hala isterse tutarlı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir görünüm korumak için varolan simgeleri kullanabilirsiniz.

 Hizmet, <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>VSPackage'ın isteğe bağlı olarak uygulayabileceği ve IDE tarafından isteneceği bir arabirimi destekler. IDE bir istekte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bulunduğunda, bu arabirimi şu anda kayıtlı olan kaynak denetimi VSPackage'den almaya çalışacaktır. Arayüz kayıtlı VSPackage'da varsa, IDE'nin özel glifler için isteği başarılı olur; aksi takdirde, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE varsayılan glifler kümesini kullanır.

 Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> çeşitli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetim durumlarını gösteren görüntülerin listesini elde etmek için kullanılır. Kaynak denetimi VSPackage, özel glifleri için görüntü listesine bir tanıtıcıyı IDE'ye döndürür. IDE bu noktada resim listesinin bir kopyasını yapar ve daha sonra görüntülemek için glifleri seçmek için kullanır. Yeni arabirim desteklenmezse veya `IVsSccGlyphs::GetCustomGlyphList` yöntem `E_NOTIMPL`döndürürse, IDE gliflerini varsayılan glifler listesinden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]alır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
