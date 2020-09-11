---
title: VSTextBuffer nesnesi | Microsoft Docs
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
ms.openlocfilehash: 856a685cbf962f8b26f77932c738c758edcf1f91
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012197"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer nesnesi
Metin buffer nesnesi, genellikle bir dosyayla ilişkili olan Unicode metin akışını temsil eder. Bir <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> nesnesi, bir sihirbaz içinde olduğu gibi çekirdek Düzenleyici 'nin bağlamı dışında kullanılabilir.

 Aşağıdaki tabloda arabirimleri gösterilmektedir `VSTextBuffer` .

|Yöntem|Açıklama|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standart OLE arabirimi. Arabellekte geri alma/yineleme işlemi için kullanılır.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standart OLE arabirimi.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Çözer eylemlerinin (yani, tek bir geri alma/yineleme biriminde gruplanmış eylemler) oluşturulmasını mümkün.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Metin arabelleği tarafından yönetilen belge verilerinin kalıcılığını mümkün hale getirme.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Temel hizmetleri sağlar; birçok istemci tarafından kullanılır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Bir arabellekte arama yapmak için kullanılır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|İki boyutlu koordinatları kullanarak okuma ve yazma özellikleri sağlar. Öğesinden devralır `IVsTextBuffer` .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Tek boyutlu koordinatları kullanarak okuma ve yazma özellikleri sağlar. Öğesinden devralır `IVsTextBuffer` .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Arabellekte metne hızlı, akışa dayalı ve sıralı erişim sağlar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Genel bir özellikler koleksiyonuna erişim sağlar. En önemli özellik, arabelleğin adı ya da adıdır. Bir GUID oluşturarak ve anahtar olarak kullanarak kendi rastgele verilerinizi bu arabirimle birlikte depolayabilmeniz gerekir.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Olaylar için bağlantı noktalarını destekler.|

## <a name="remarks"></a>Açıklamalar
 `VSTextBuffer`Genellikle `QueryInterface` üzerinde bir çağrısıyla bulunur `IVsTextBuffer` . Daha fazla bilgi için bkz. [metin arabelleği](../vs-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md?view=vs-2015).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Şekil düzenleme](https://www.microsoft.com/download/details.aspx?id=55984)