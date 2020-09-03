---
title: Glif denetimi (kaynak denetimi VSPackage) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708314"
---
# <a name="glyph-control-source-control-vspackage"></a>Glif denetimi (kaynak denetimi VSPackage)
Kaynak denetimi VSPackages tarafından kullanılabilen derin tümleştirmenin bir parçası, kaynak denetimi altındaki öğelerin durumunu göstermek için kendi gliflerini görüntüleme olanağıdır.

## <a name="levels-of-glyph-control"></a>Glif denetimi düzeyleri
 Durum karakteri, örneğin **Çözüm Gezgini** veya **sınıf görünümü**gibi, görüntülendiğinde bir öğenin geçerli durumunu gösteren bir simgedir. Kaynak denetimi VSPackage iki karakter düzeyi denetimi uygulayabilir. Karakter seçimini IDE tarafından sunulan önceden tanımlanmış bir karakter kümesiyle sınırlayabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] veya görüntülenecek özel bir glif kümesi tanımlayabilir.

### <a name="default-set-of-glyphs"></a>Varsayılan glif kümesi
 Bir proje, **Çözüm Gezgini**bir öğeyle ilişkili olan durum glifleri tespit etmek için, kullanarak kaynak denetiminden durum glifi ister <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> . Kaynak denetimi VSPackage, IDE tarafından sunulan önceden tanımlanmış glifle sınırlı karakter seçimini tutmaya karar verebilir. Bu durumda, VSPackage, *vsshell. IDL*dosyasında tanımlanan glif numaralandırmaları temsil eden bir değer dizisini geri geçirir. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Bu, giriş karakteri için bir asma kilidi ve kullanıma hazır karakter için bir onay işareti gibi, IDE tarafından ayarlanan, önceden tanımlanmış bir karakter kümesidir.

### <a name="custom-set-of-glyphs"></a>Özel glif kümesi
 Kaynak denetimi VSPackage, yüklendiğinde benzersiz bir görünüm ve kullanım için kendi gliflerinden yararlanabilirsiniz. Yeni bir kaynak denetimi VSPackage etkinken, önceki bir kaynak denetimi VSPackage hala yüklenmiş ancak devre dışı olsa bile kendi glifleri kullanmaya başlayabilmelidir. Bu modda, kaynak denetimi VSPackage hala, seçerse tutarlı bir görünüm sağlamak için var olan simgeleri kullanabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>Hizmet, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> VSPackage 'ın isteğe bağlı olarak uygulayabileceği ve IDE tarafından istenecek bir arabirimi destekler. IDE bir istek yaptığında, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Bu arabirimi şu anda kayıtlı kaynak denetiminden almaya çalışır. Arabirim kayıtlı VSPackage içinde varsa, IDE 'nin özel Glifler isteği başarılı olur; Aksi halde, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE varsayılan glif kümesini kullanır.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>Yöntemi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çeşitli kaynak denetimi durumlarını gösteren görüntülerin bir listesini almak için tarafından kullanılır. Kaynak denetimi VSPackage, özel glifleri için görüntü listesine yönelik bir tutamacı IDE 'ye geri döndürür. IDE, bu noktada görüntü listesinin bir kopyasını oluşturur ve daha sonra görüntülenecek glifleri seçmek için onu kullanır. Yeni arabirim desteklenmiyorsa veya `IVsSccGlyphs::GetCustomGlyphList` Yöntem döndürüyorsa `E_NOTIMPL` , IDE, tarafından sağlanan varsayılan glif listesinden kendi glifleri alır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
