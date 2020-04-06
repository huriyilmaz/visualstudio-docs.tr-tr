---
title: Belge Pencereleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711033a4ad2e782ecbe509595266426d186bed8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708511"
---
# <a name="document-windows"></a>Belge pencereleri
Visual Studio'da *belge penceresi,* birden çok belge arabirimi (MDI) penceresiyle ilişkili çerçeveli bir alt penceredir. Belge pencereleri genellikle kaynak kodun veya metnin görüntülenmesi ve değiştirilmesi için kullanılır, ancak diğer işlevsel türleri de barındırabilir. Belge pencereleri:

- Birden çok dosyanın aynı anda görüntülenebilmeleri için üst MDI'deki ayrı yatay veya dikey sekme gruplarında düzenlenebilir.

- Ana MDI'de herhangi bir sırada kenetlenebilir.

- Serbestçe yüzebilir.

- Sekme sırasına göre diğer MDI pencerelerine bağlanır.

  Gruplandırma, yerleştirme ve kayanlık komutları belge penceresi sekmesinin kısayol menüsünde bulunabilir.

  Visual Studio'daki pencere davranışı hakkında daha fazla bilgi için [bkz.](../../ide/customizing-window-layouts-in-visual-studio.md)

## <a name="document-window-implementation"></a>Belge penceresi uygulaması
 Belge pencereleri bir düzenleyici uygulanarak oluşturulur. Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> bir düzenleyiciyi anlık olarak oluşturmanın bir parçası olarak belge pencereleri oluşturur. Daha fazla bilgi için [editördeki Eski arabirimleri'ne](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)bakın.

> [!NOTE]
> Bir pencerede ileri ve geri gezinme <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> noktaları sağlamak için arabirimi uygulayın. Metin düzenleyicisi, belgedeki gezinti noktalarını tanımlamak için metin işaretçileri kullanır.

## <a name="the-running-document-table"></a>Çalışan belge tablosu
 IDE, her belge penceresinin durumunu izlemek için Çalışan belge tablosunu (RDT) kullanır. RDT, çözüm kapatıldığında veya dosya nın düzenlendiği nde olduğu gibi belge pencerelerinin olaylardan haberdar edildiği mekanizmadır. Daha fazla bilgi için [bkz.](../../extensibility/internals/running-document-table.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Gecikmiş belge yükleme](../../extensibility/internals/delayed-document-loading.md)
