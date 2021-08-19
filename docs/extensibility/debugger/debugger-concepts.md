---
title: Hata ayıklayıcı kavramları | Microsoft Docs
description: bu pakette derleme yapmanıza yardımcı olmak üzere Visual Studio hata ayıklama paketini tasarlarken kullanılan mimari kavramlar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 2d407418d158adbd06dd64f998a1c6831b9f7cd1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133243"
---
# <a name="debugger-concepts"></a>Hata ayıklayıcı kavramları
Visual Studio hata ayıklama paketini oluşturmak için, paketi tasarlarken kullanılan mimari kavramlara alışmalısınız.

## <a name="in-this-section"></a>Bu bölümde
 [Hata ayıklama oturumu](../../extensibility/debugger/debug-session.md) Hata ayıklama mimarisinde bir oturumun rolünü açıklar.

 [Sunucular](../../extensibility/debugger/servers-visual-studio-sdk.md) Bir sunucunun hata ayıklama mimarisi açısından, hem soyut hem de fiziksel koşullarda ne olduğunu tanımlar.

 [Bağlantı noktası tedarikçileri](../../extensibility/debugger/port-suppliers.md) Bir bağlantı noktası tedarikçinin hata ayıklama mimarisi açısından ne olduğunu tanımlar.

 [Bağlantı noktaları](../../extensibility/debugger/ports.md) Bir bağlantı noktasının hata ayıklama mimarisi açısından ne olduğunu tanımlar.

 [Süreçler](../../extensibility/debugger/processes.md) Bir işlemin hata ayıklama mimarisi açısından ne olduğunu tanımlar.

 [Program düğümleri](../../extensibility/debugger/program-nodes.md) Bir program düğümünü, hata ayıklama mimarisi açısından, kendisini ve üzerinde çalıştığı işlemi nasıl tanımlayabileceğini de içerecek şekilde tanımlar.

 [Programlar](../../extensibility/debugger/programs.md) Hata ayıklama mimarisi açısından bir program tanımlar.

 [Iş parçacıkları](../../extensibility/debugger/threads.md) Hata ayıklama mimarisi açısından iş parçacıklarının özelliklerini tanımlar.

 [Yığın çerçeveleri](../../extensibility/debugger/stack-frames.md) Hata ayıklama mimarisi bakımından bir yığın çerçevesini tanımlar. Yığın çerçevesi, bir iş parçacığının Yürütme bağlamını sağlayan bir yığın soyutlamasıdır.

 [Modüller](../../extensibility/debugger/modules.md) Hata ayıklama mimarisi açısından, yürütülebilir dosya veya DLL gibi bir fiziksel kod kapsayıcısı olarak bir modülü tanımlar.

 [Kesme noktaları](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Hata ayıklama mimarisi açısından, bekleyen, bağlantılı ve hata gibi üç kesme noktası türünü tanımlar.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md) Hata ayıklama altyapısının (DE) kod, belge ve ifade değerlendirme bağlamlarının eşzamanlı olarak nasıl çalıştığını açıklar. Üç bağlamın her biri için, bu konuyla ilgili konum, konum veya değerlendirmeyi açıklar.

 [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md) hata ayıklama altyapısını (DE), ifade değerlendirici (EE) ve sembol işleyicisini (SH) içeren Visual Studio hata ayıklama bileşenlerine genel bakış sağlar.

 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md) Bir program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerinin bağlantılarını içerir.
