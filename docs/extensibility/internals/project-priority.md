---
title: Proje Önceliği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a75c1c333d88e1bf5524281bee8b2a683ca6c98e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706414"
---
# <a name="project-priority"></a>Proje Önceliği
Proje öğesi genellikle çözümdeki yalnızca bir projenin üyesidir. Bu nedenle, IDE öğeyi açmak için hangi projenin kullanıldığını kolayca belirleyebilir. Ancak, bir öğe birden fazla projenin üyesiyse, IDE öğeyi açmak için en iyi projeyi belirlemek için bir öncelik düzeni kullanır.

 Aşağıdaki liste proje öncelik düzenini gösterir:

- IDE, belgenin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> o projenin bir üyesi olup olmadığını belirlemek için çözümdeki her proje yöntemini çağırır.

- Belge projenin bir üyesiyse, proje, projenin bu belgeyi işlemesine göre atadığı bir öncelikle yanıt verir. Örneğin, bir dil projesi dil kaynağı dosyaları için yüksek bir önceliğe sahip yanıt verir, ancak yapı işleminin bir parçası olarak kullanılmayan tanınmayan bir dosya türü için daha düşük bir öncelikle yanıt verir.

- Bir belge için özel, projeye özel düzenleyiciler veya tasarımcılar sağlayan projeler de yüksek öncelik alır.

- Numaralandırma belge <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> öncelik değerlerini sağlar.

- En yüksek önceliği belirten projeye belgeyi açmak için bağlam verilir. İki proje eşit öncelik değerleri döndürürse, etkin proje tercih edilir. Çözümdeki hiçbir proje belgeyi açabileceği yanıtını vermezse, IDE belgeyi Çeşitli Dosyalar projesine koyar. Daha fazla bilgi için [bkz.](../../extensibility/internals/miscellaneous-files-project.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Çeşitli Dosyalar Projesi](../../extensibility/internals/miscellaneous-files-project.md)
- [Nasıl Yapılır: Açık Belgeler için Düzenleyicileri Açma](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
