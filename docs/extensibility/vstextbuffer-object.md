---
title: VSTextBuffer Nesne | Microsoft Docs
description: VSTextBuffer nesnesi, genellikle bir dosyayla ilişkilendirilmiş bir Unicode metin akışını temsil eder. Bu makalede VSTextBuffer'ın arabirimleri listeleniyor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3660a8dbb4a0a1280d5a3f428f73f3498244af7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905182"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer nesnesi
Metin arabelleği nesnesi, genellikle bir dosyayla ilişkilendirilmiş bir Unicode metin akışını temsil eder. Nesne, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> sihirbazda olduğu gibi çekirdek düzenleyicinin bağlamı dışında kullanılabilir.

 Aşağıdaki tabloda arabirimleri `VSTextBuffer` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[ıolecommandtarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standart OLE arabirimi. Arabellekte geri alma/yenidendo işleme için kullanılır.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standart OLE arabirimi.|
|[ıpersiststream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Etkili eylemlerin (tek bir geri alma/yenidendo biriminde gruplandı) oluşturulmasını sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Metin arabelleği tarafından yönetilen belge verileri kalıcılığı sağlar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Temel hizmetler sağlar; birçok istemci tarafından kullanılır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Arabellekte arama yapmak için kullanılır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|İki boyutlu koordinatları kullanarak okuma ve yazma özellikleri sağlar. 'den `IVsTextBuffer` devralıyor.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Tek boyutlu koordinatları kullanarak okuma ve yazma özellikleri sağlar. 'den `IVsTextBuffer` devralıyor.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Arabellekte metne hızlı, akış odaklı, sıralı erişim sağlar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Genel bir özellik koleksiyonuna erişim sağlar. En önemli özellik, arabelleğin adı veya bilinen adıdır. Guid oluşturarak ve anahtar olarak kullanarak kendi rastgele verilerinizi bu arabirimle arabellekte depoabilirsiniz.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Olaylar için bağlantı noktalarını destekler.|

## <a name="remarks"></a>Açıklamalar
 genellikle `VSTextBuffer` üzerinde bir çağrısı tarafından `QueryInterface` `IVsTextBuffer` bulunur. Daha fazla bilgi için [bkz. Metin arabelleği.](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Şekiller düzenleme](https://www.microsoft.com/download/details.aspx?id=55984)