---
title: Project Öncelik | Microsoft Docs
description: IDE'nin kullandığı öncelik Visual Studio öğe birden fazla projenin üyesi ise bir öğeyi açmak için en iyi projeyi belirlemesini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9a6b804836daffbd0520ed83fd9d1f6d1fa9b566
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049720"
---
# <a name="project-priority"></a>Proje Önceliği
Proje öğesi genellikle çözümde yalnızca bir projenin üyesidir. Bu nedenle IDE, öğeyi açmak için kullanılan projeyi kolayca belirler. Ancak, bir öğe birden fazla projenin üyesi ise IDE, öğeyi açmak için en iyi projeyi belirlemek üzere bir öncelik şeması kullanır.

 Aşağıdaki listede proje öncelik şemasını gösterir:

- IDE, belgenin o projenin üyesi olup olmadığını belirlemek için çözümde yer <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> alan her bir proje için yöntemini çağırarak.

- Belge projenin bir üyesi ise proje, projenin bu belgenin işlenmesine göre atadığınız bir öncelikle yanıt verir. Örneğin bir dil projesi, dil kaynak dosyaları için yüksek öncelikli yanıt verir ancak derleme işleminin bir parçası olarak kullanılmayan tanınmayan bir dosya türü için daha düşük önceliğe sahip yanıt verir.

- Bir belge için özel, projeye özgü düzenleyiciler veya tasarımcılar sağlayan projeler de yüksek önceliklidir.

- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>Numaralama, belge öncelik değerlerini sağlar.

- En yüksek önceliği belirten projeye belgeyi açmak için bağlam verilir. İki proje eşit öncelik değerlerine sahipse etkin proje tercih edilir. Çözümde belgeyi açarak yanıt veren bir proje yoksa, IDE belgeyi Çeşitli Dosyalar projesine koyar. Daha fazla bilgi için [bkz. Çeşitli Dosyalar Project.](../../extensibility/internals/miscellaneous-files-project.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Çeşitli Dosyalar Projesi](../../extensibility/internals/miscellaneous-files-project.md)
- [Nasıl Yapılır: Açık Belgeler için Düzenleyicileri Açma](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
