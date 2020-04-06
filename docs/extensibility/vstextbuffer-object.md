---
title: VSTextBuffer Nesne | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ea44d2b22c96d49f334f2ea33f9db8d69b5eb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697720"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer nesnesi
Metin arabelleği nesnesi, genellikle bir dosyayla ilişkili olan Unicode metin akışını temsil eder. Bir <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> nesne, bir sihirbaz gibi çekirdek düzenleyicibağlamının dışında kullanılabilir.

 Aşağıdaki tabloda `VSTextBuffer`.

|Yöntem|Açıklama|
|------------|-----------------|
|[ıolecommandtarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standart OLE arabirimi. Arabellekte geri alma/yeniden yapma işleme için kullanılır.|
|[IpersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standart OLE arabirimi.|
|[ıpersiststream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Bileşik eylemlerin (diğer bir deyişle, tek bir geri/yeniden oluşturma biriminde gruplanan eylemler) oluşturulmasını sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Metin arabelleği tarafından yönetilen belge verilerinin kalıcılığını sağlar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Temel hizmetler sağlar; birçok istemci tarafından kullanılır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Arabelleği aramak için kullanılır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|İki boyutlu koordinatları kullanarak okuma ve yazma yetenekleri sağlar. 'den `IVsTextBuffer`miras alır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Tek boyutlu koordinatları kullanarak okuma ve yazma yetenekleri sağlar. 'den `IVsTextBuffer`miras alır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Arabellekteki metne hızlı, akış odaklı, sıralı erişim sağlar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Genel bir özellik koleksiyonuna erişim sağlar. En önemli özellik arabelleğeanın adı veya takma adıdır. Bir GUID oluşturup anahtar olarak kullanarak bu arabirimle kendi rasgele verilerinizi arabellekte depolayabilirsiniz.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Olaylar için bağlantı noktalarını destekler.|

## <a name="remarks"></a>Açıklamalar
 Genellikle `VSTextBuffer` bir `QueryInterface` çağrı ile `IVsTextBuffer`bulunur. Daha fazla bilgi için [Metin arabelleği'ne](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Şekiller edit](https://www.microsoft.com/download/details.aspx?id=55984)
