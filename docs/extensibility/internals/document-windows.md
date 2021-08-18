---
title: Belge Windows | Microsoft Docs
description: Uygulama ve Çalışan belge Visual Studio (RDT) durumlarını nasıl takip etmek de dahil olmak üzere, belge pencerelerini nasıl uygulayacaklarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1a1659bc97e1626e198b2a3867223005c84cf9e7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094886"
---
# <a name="document-windows"></a>Belge pencereleri
Bu Visual Studio belge *penceresi,* çok belgeli arabirim (MDI) penceresiyle ilişkili çerçeveli bir alt penceredir. Belge pencereleri genellikle kaynak kodun veya metnin görüntüsü ve değişikliği için kullanılır, ancak diğer işlev türlerini de barındırabilir. Belge pencereleri:

- Üst MDI'da ayrı yatay veya dikey sekme gruplarında düzenleniyor, böylece aynı anda birden çok dosya görüntüleniyor olabilir.

- Üst MDI'de herhangi bir sırada yer alan olabilir.

- Serbestçe kayan olabilir.

- Diğer MDI pencerelere sekme sırasıyla bağlıdır.

  Gruplama, yerleştirme ve kayan öğe komutları, belge penceresi sekmesinin kısayol menüsünde bulunabilir.

  Uygulama içinde pencere davranışı hakkında daha fazla Visual Studio için [bkz. Pencere düzenlerini özelleştirme.](../../ide/customizing-window-layouts-in-visual-studio.md)

## <a name="document-window-implementation"></a>Belge penceresi uygulaması
 Belge pencereleri bir düzenleyici uygulanarak oluşturulur. Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> bir düzenleyici örneği oluşturmanın bir parçası olarak belge pencereleri oluşturur. Daha fazla bilgi için [bkz. Düzenleyicide eski arabirimler.](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)

> [!NOTE]
> Bir pencerede geriye ve ileriye doğru gezinti noktaları sağlamak için arabirimini <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> kullanın. Metin düzenleyicisi, belgede gezinti noktalarını tanımlamak için metin işaretçilerini kullanır.

## <a name="the-running-document-table"></a>Çalışan belge tablosu
 IDE, her belge penceresinin durumunu izlemek için Çalışan belge tablosu (RDT) kullanır. RDT, belge pencerelerinin bir çözümün kapatılan veya bir dosya düzenlenmiş olduğu gibi olaylar hakkında bilgi veren mekanizmadır. Daha fazla bilgi için [bkz. Belge tablosu çalıştırma.](../../extensibility/internals/running-document-table.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Belge yüklemesi geciktirildi](../../extensibility/internals/delayed-document-loading.md)
