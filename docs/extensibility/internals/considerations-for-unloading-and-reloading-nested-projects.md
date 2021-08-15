---
title: İç içe projeleri kaldırma ve yeniden yükleme
description: İç içe geçmiş projeleri yüklemeden kaldırma ve yeniden yükleme sırasında gerçekleştirecekleri ek adımları Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0bc43f6ee9896df550b1eb152fb1a0eb576b515813ea28a03d3a61e3877dbdcd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432623"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>İç içe projeleri kaldırma ve yeniden yükleme ile ilgili önemli noktalar

İç içe proje türlerini uygulamak için projeleri kaldırma ve yeniden yükleme adımlarını gerçekleştirmeniz gerekir. Çözüm olaylarını dinleyicilere doğru şekilde bildirmek için ve olaylarını doğru şekilde `OnBeforeUnloadProject` yükseltmeniz `OnAfterLoadProject` gerekir.

Bu olayları nedenlerinden biri kaynak kodu denetimidir (SCC). SCC'nin öğeleri sunucudan silebilir ve ardından SCC'den bir işlem varsa bunları yeni olarak yeniden  `Get` eklemesi istemiyorsanız. Bu durumda, SCC'den yeni bir dosya yüklenir. Farklı olduğu durumda tüm dosyaları kaldırmalı ve yeniden yükleyebilirsiniz.

Kaynak kodu denetimi çağrısında `ReloadItem` bulundu. Projeyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> silmek ve yeniden `OnBeforeUnloadProject` oluşturmak için ve çağrısı yapmak için `OnAfterLoadProject` arabirimini uygulama. Arabirimi bu şekilde uygulayan SCC, projenin geçici olarak silindiğini ve yeniden eklenmiştir. Bu nedenle, SCC proje üzerinde proje gerçekten silinmiş ve yeniden *eklenmiş* gibi çalışmaz.

## <a name="reload-projects"></a>Projeleri yeniden yükleme

İç içe projelerin yeniden yüklerini desteklemek için yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> kullanırsiniz. uygulamasında, `ReloadItem` iç içe geçmiş projeleri kapatıp yeniden oluşturmanız gerekir.

Genellikle bir proje yeniden yüklendiğinde, IDE ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> olaylarını <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> yükselter. Ancak, silinen ve yeniden yüklenen iç içe projeler için, üst proje IDE'nin değil işlemi başlatıyor. Üst proje çözüm olaylarını başlatmaz ve IDE'nin sürecin başlatıla ilgili bilgisi yoktur, olaylar gerçekleşmez.

Bu işlemi işlemek için üst proje `QueryInterface` arabirimini <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> çağırır. `IVsFireSolutionEvents` , IDE'ye iç içe projeyi kaldırması için olayı yükseltmesini ve ardından aynı projeyi yeniden yüklemek için `OnBeforeUnloadProject` `OnAfterLoadProject` olayı yükseltmesini söyler.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Projeleri iç içe yerleştirme](../../extensibility/internals/nesting-projects.md)
