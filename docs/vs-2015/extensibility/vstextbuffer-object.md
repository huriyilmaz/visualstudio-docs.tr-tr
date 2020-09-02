---
title: VSTextBuffer nesnesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b68d443e542b6bd707aacc2b22d0efc1064152c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690638"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer Nesnesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin buffer nesnesi, genellikle bir dosyayla ilişkili olan Unicode metin akışını temsil eder. Bir <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> nesne, bir sihirbaz durumunda olduğu gibi çekirdek Düzenleyici 'nin bağlamı dışında kullanılabilir.  
  
 Aşağıdaki tabloda arabirimleri gösterilmektedir `VSTextBuffer` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standart OLE arabirimi. Genellikle arabellekte geri alma/yineleme işlemi için kullanılır.|  
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
 `VSTextBuffer`Genellikle `QueryInterface` üzerinde bir çağrısıyla bulunur `IVsTextBuffer` . Daha fazla bilgi için bkz. [metin arabelleği](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Şekil düzenleme](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
