---
title: Hata ayıklama görevleri | Microsoft Docs
description: Hata ayıklama altyapısına ekleme, başlangıç olayları oluşturma ve kesme noktalarına ulaşma gibi bir programda hata ayıklamak için gereken görevler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 960e87e629caca705d8dc8e8fd54de3731b9604e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096706"
---
# <a name="debug-tasks"></a>Hata ayıklama görevleri
Bir programda hata ayıklamak için, başlatılmalıdır ve buna bir hata ayıklama altyapısı (DE) eklenmelidir, aksi takdirde DE daha önce başlatılmış bir programa eklenmelidir. İliştirildikten sonra, belirli başlangıç olaylarını üretmelidir. Yanıt olarak, hata ayıklama paketi IDE 'de ayarlanan kesme noktalarını bağlamaya çalışır. Program, bağlantılı bir kesme noktasına rastarsa, durdurur ve Kullanıcı girişini bekler.

## <a name="in-this-section"></a>Bu bölümde
 [Güvenlik sorunları](../../extensibility/debugger/security-issues.md) Bir programın hatalarını ayıklamak için gereken güvenlik adımlarını açıklar.

 [Program başlatma](../../extensibility/debugger/launching-a-program.md) Programı başlatmak için işletim sistemini çağıran bir DE belirtme hakkında adım adım yönergeler sağlar.

 [Doğrudan bir programa iliştirme](../../extensibility/debugger/attaching-directly-to-a-program.md) Zaten çalışmakta olan bir işlemdeki programda hata ayıklamak için kullanılan süreci açıklar.

 Başlatma [sonrasında başlangıç olaylarını gönder](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Program ana giriş noktasına gelene ve hata ayıklama için hazırlanana kadar,, programa eklendikten sonra gerçekleşmekte olan olayları listeler.

 [Yürütmenin denetimi](../../extensibility/debugger/control-of-execution.md) , Koşullara bağlı olarak genellikle bir giriş noktası olayını, yük-tam olayı veya durdurma olayını nasıl göndereceğini açıklar.

 [Bağlama kesme noktaları](../../extensibility/debugger/binding-breakpoints.md) Kullanıcı bir kesme noktası ayarladıysanız, IDE 'nin isteği nasıl oluşturup hata ayıklama oturumunda kesme noktası oluşturmasını isteyip isteyebileceğinizi açıklar.

 [Ifadeleri değerlendir](../../extensibility/debugger/evaluating-expressions.md) İfadelerin nasıl oluşturulduğunu ve bir ifadenin değerlendirildiği zaman ne olacağını açıklar.

 [Verileri görselleştirme ve görüntüleme](../../extensibility/debugger/visualizing-and-viewing-data.md) Tür görselleştiricilerin ve özel görüntüleyicilerin ifade değerlendirici (EE) tarafından nasıl desteklendiği açıklanmaktadır.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimarisi kavramlarını açıklar.

 [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md) Visual Studio hata ayıklama bileşenlerine genel bir bakış sağlar, bu, EE ve sembol işleyicisini (SH) içerir.

 [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md) Aynı anda kod, belge ve ifade değerlendirme bağlamlarının içinde nasıl çalıştığını açıklar. Üç bağlamın her biri için, bu konuyla ilgili konum, konum veya değerlendirmeyi açıklar.

## <a name="see-also"></a>Ayrıca bkz.
 [Kullanmaya başlama](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
