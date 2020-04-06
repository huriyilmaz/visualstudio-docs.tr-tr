---
title: Hata Ayıklama Görevleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d41f53ab1392ea3c31908faf65a871fa100fbb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738963"
---
# <a name="debug-tasks"></a>Hata ayıklama görevleri
Bir programı hata ayıklamak için başlatılmalı ve hata ayıklama altyapısı (DE) eklenmelidir veya başka bir şekilde DE daha önce başlatılan bir programa eklenmelidir. Bağlandıktan sonra, DE belirli başlangıç olayları oluşturmalıdır. Buna yanıt olarak, hata ayıklama paketi IDE'de ayarlanan kesme noktalarını bağlamaya çalışır. Program bağlı bir kesme noktasına ulaştığında durur ve kullanıcı girişini bekler.

## <a name="in-this-section"></a>Bu bölümde
 [Güvenlik sorunları](../../extensibility/debugger/security-issues.md) Bir programı hata ayıklamak için gereken güvenlik adımlarını tartışır.

 [Bir program başlatın](../../extensibility/debugger/launching-a-program.md) Programı başlatmak için işletim sistemini çağıran bir DE'nin nasıl belirtilen hakkında adım adım yönergeler sağlar.

 [Doğrudan bir programa ekleme](../../extensibility/debugger/attaching-directly-to-a-program.md) Zaten çalışmakta olan bir işlemde bir programı hata ayıklamak için kullanılan işlemi açıklar.

 [Başlatmadan sonra başlangıç olaylarını gönderme](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Program ana giriş noktasında olana ve hata ayıklama için hazır olana kadar DE programa iliştirildikten sonra gerçekleşen olayları listeler.

 [Yürütmenin kontrolü](../../extensibility/debugger/control-of-execution.md) DE'nin koşullara bağlı olarak bir giriş noktası olayını, yükleme tamamlama olayını veya durdurma olayını nasıl gönderdiğini açıklar.

 [Kesme noktalarını bağlama](../../extensibility/debugger/binding-breakpoints.md) Kullanıcı bir kesme noktası ayarlarsa, IDE'nin isteği nasıl formüle ettiği ve hata ayıklama oturumunu kesme noktasını oluşturması nasıI istendiğini açıklar.

 [İfadeleri değerlendirme](../../extensibility/debugger/evaluating-expressions.md) İfadelerin nasıl oluşturulduğunu ve bir ifade değerlendirildiğinde ne olacağını açıklar.

 [Verileri görselleştirme ve görüntüleme](../../extensibility/debugger/visualizing-and-viewing-data.md) Tür görselleştiricilerinin ve özel görüntüleyenlerin ifade değerlendiricisi (EE) tarafından nasıl desteklenirlerini açıklar.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimari kavramları açıklar.

 [Hata ayıklama bileşenleri](../../extensibility/debugger/debugger-components.md) DE, EE ve sembol işleyicisini (SH) içeren Visual Studio hata ayıklama bileşenlerine genel bir bakış sağlar.

 [Hata ayıklama bağlamları](../../extensibility/debugger/debugger-contexts.md) DE'nin kod, belge ve ifade değerlendirme bağlamlarında aynı anda nasıl çalıştığını açıklar. Üç bağlamın her biri için, bununla ilgili konumu, konumu veya değerlendirmeyi açıklar.

## <a name="see-also"></a>Ayrıca bkz.
 [başlarken](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
