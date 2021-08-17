---
title: Belge Windows | Microsoft Docs
description: Visual Studio ' deki belge pencereleri hakkında bilgi edinin ve bunları nasıl uygulayacağınızı ve çalışan belge tablosunun (rdt) durumlarını nasıl izlediğini öğrenin.
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
ms.openlocfilehash: fc3fc77d895805eae1dbffb092721fc0c8dd616c63b796da42205e1e65c42ea9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376254"
---
# <a name="document-windows"></a>Belge pencereleri
Visual Studio, *belge penceresi* bir çoklu belge arabirimi (mdı) penceresiyle ilişkili olan bir çerçeveli alt penceredir. Belge pencereleri genellikle kaynak kodu veya metin görüntüleme ve değiştirme için kullanılır, ancak diğer işlevsel türleri de barındırabilir. Belge pencereleri:

- Aynı anda birden çok dosya görüntülenebilmesi için üst MDI 'daki ayrı yatay veya dikey sekme grupları halinde düzenlenebilir.

- Üst MDI 'da herhangi bir sıraya yerleştirilebilir.

- Serbestçe eklenebilir.

- , Diğer MDI pencereleri için sekme sırasıyla bağlantılıdır.

  Gruplandırma, yerleştirme ve kayan komutlar, bir belge penceresi sekmesi için kısayol menüsünde bulunabilir.

  Visual Studio pencere davranışı hakkında daha fazla bilgi için bkz. [özelleştirme pencere düzenleri](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Belge penceresi uygulama
 Belge pencereleri bir düzenleyici uygulayarak oluşturulur. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>Arabirim, bir düzenleyiciyi örnekleyici belge pencerelerini oluşturur. Daha fazla bilgi için bkz. [düzenleyicideki eski arabirimler](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015).

> [!NOTE]
> Bir pencerede geri ve İleri gezinti noktaları sağlamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> arabirimini uygulayın. Metin Düzenleyicisi belgedeki gezinti noktalarını tanımlamak için metin işaretçilerini kullanır.

## <a name="the-running-document-table"></a>Çalışan belge tablosu
 IDE, her belge penceresinin durumunu izlemek için çalışan belge tablosunu (RDT) kullanır. RDT, bir çözümün ne zaman kapatıldığı veya bir dosyanın düzenlenmediği gibi, Belge pencerelerinin hangi olaylar hakkında bilgilendirilmesine yönelik bir mekanizmadır. Daha fazla bilgi için bkz. [çalışma belge tablosu](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Gecikmeli belge yükleme](../../extensibility/internals/delayed-document-loading.md)
