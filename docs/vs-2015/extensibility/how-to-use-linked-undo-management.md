---
title: 'Nasıl yapılır: bağlı geri alma yönetimini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67d0d173909b8cdfe2eaf0d56aa5c99c437d5ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795512"
---
# <a name="how-to-use-linked-undo-management"></a>Nasıl Yapılır: Bağlantılı Geri Alma Yönetimini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bağlı geri alma, kullanıcının birden çok dosyada aynı düzenlemeleri aynı anda geri almasına izin verir. Örneğin, bir üstbilgi dosyası ve bir Visual C++ dosyası gibi birden çok program dosyasında eşzamanlı metin değişiklikleri, bağlantılı bir geri alma işlemi olur. Bağlı geri alma özelliği, ortamın geri alma Yöneticisi uygulamasında yerleşiktir ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> Bu özelliği değiştirmenize olanak sağlar. Bağlı geri alma, tek bir geri alma birimi olarak değerlendirilecek şekilde ayrı geri alma yığınları birbirine bağlayabileceğiniz bir üst geri alma birimi tarafından uygulanır. Bağlı geri alma kullanma yordamı aşağıdaki bölümde ayrıntılı olarak verilmiştir.  
  
### <a name="to-use-linked-undo"></a>Bağlı geri almayı kullanmak için  
  
1. `QueryService`' `SVsLinkedUndoManager` A bir işaretçi almak için öğesini çağırın `IVsLinkedUndoTransactionManager` .  
  
2. Çağırarak ilk üst bağlantılı geri alma birimini oluşturun <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> . Bu, geri alma yığınları kümesi için başlangıç noktasını, bağlantılı geri alma yığınlarıyla gruplandırılacak şekilde ayarlar. Yönteminde, `OpenLinkedUndo` bağlantılı geri alma 'nın katı mi yoksa katı olmayan mı olacağını da belirtmeniz gerekir. Kesin olmayan bağlantılı geri alma davranışı, bağlı geri alma eşdüzey öğelerinin bazı belgelerinin kapatılacağını ve yine de yığınlarındaki diğer bağlı geri alma eşdeğerlerini bırakabilmesini sağlayabilir. Kesin bağlantılı geri alma davranışı, tüm bağlı geri alma eşdüzey yığınlarının birlikte geri alınması veya hiç olmaması gerektiğini belirtir. [IOleUndoManager:: Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) metodunu çağırarak sonraki bağlantılı geri alma yığınlarını ekleyin.  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A>Bağlı geri alma birimlerinin tümünü bir tane olarak geri almak için çağırın.  
  
    > [!NOTE]
    > Bağlı geri alma yönetimini bir düzenleyicide uygulamak için, geri alma yönetimi ekleyin. Bağlı geri alma yönetimini uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: geri alma yönetimini](../extensibility/how-to-implement-undo-management.md)uygulama.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Nasıl Yapılır: Geri Alma Yönetimini Uygulama](../extensibility/how-to-implement-undo-management.md)
