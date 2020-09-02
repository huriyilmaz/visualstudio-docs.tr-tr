---
title: Proje önceliği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b012136c30f72cfdddadfc1a370ed76f567afffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429918"
---
# <a name="project-priority"></a>Proje Önceliği
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proje öğesi genellikle çözümdeki yalnızca bir projenin üyesidir. Bu nedenle, IDE, öğeyi açmak için hangi projenin kullanıldığını kolayca belirleyebilir. Ancak, bir öğe birden fazla projenin üyesiyse, IDE, öğeyi açmak için en iyi projeyi belirlemede bir öncelik şeması kullanır.  
  
 Aşağıdaki listede, proje öncelik şeması gösterilmektedir:  
  
- IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> belgenin o projenin bir üyesi olup olmadığını anlamak için çözümdeki her proje için yöntemini çağırır.  
  
- Belge projenin üyesiyse proje, projenin işleme göre atadığı bir öncelik ile yanıt verir. Örneğin, bir dil projesi kendi dil kaynak dosyaları için yüksek öncelikli olarak yanıt verir, ancak yapı sürecinin bir parçası olarak kullanılmayan tanınmayan bir dosya türü için daha düşük bir önceliğe sahip olur.  
  
- Bir belge için özel, projeye özgü düzenleyiciler ve tasarımcılar sağlayan projeler de yüksek öncelikli bir öncelik alır.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>Sabit listesi belge önceliği değerlerini sağlar.  
  
- En yüksek önceliğe sahip projeye belgeyi açmak için bağlam verilir. İki proje eşit öncelik değeri getirse, etkin proje tercih edilir. Çözümdeki bir proje belgeyi açabiliyorsa yanıt verirse, IDE belgeyi çeşitli dosyalar projesine koyar. Daha fazla bilgi için bkz. [çeşitli dosyalar projesi](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çeşitli dosyalar projesi](../../extensibility/internals/miscellaneous-files-project.md)   
 [Nasıl yapılır: açık belgeler için düzenleyiciler açma](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
