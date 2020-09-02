---
title: Bağlam menüleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9baab8ef64fa1952eff138165f608e25960c8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184272"
---
# <a name="context-menus"></a>Bağlam Menüleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bağlam menüleri, bir kullanıcı istemci alanının etkin bir bölgesine sağ tıkladığında ve sağ fare düğmesi serbest bırakıldığında ' i seçtiğinde görüntülenir.  
  
## <a name="editor-context-menus"></a>Düzenleyici Bağlam Menüleri  
 `ECMD_SHOWCONTEXTMENU`Bu işlem, dil hizmetiniz düzenleyicide görüntülenecek bağlam menülerini denetleyebilir. Kendi bağlam menünüzün görüntülenmesini sağlamak için, bu komutu çağırarak öğesine geçirildiğinde işleyin <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> . Bu komutu işlemeyin, IDE, düzenleyici için sunulan standart bağlam menüsünü görüntüler. Bağlam menüsünün içeriğini işaret başına temelinde da denetleyebilirsiniz. Bunun hakkında daha fazla bilgi için, bkz. [eskı API Ile metin Işaretleyicileri kullanma](../extensibility/using-text-markers-with-the-legacy-api.md) ve [eski dil hizmeti ile kesintiye uğratan hizmet komutları](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmeti geliştirme](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Menüleri ve Komutlari Genişletme](../extensibility/extending-menus-and-commands.md)
