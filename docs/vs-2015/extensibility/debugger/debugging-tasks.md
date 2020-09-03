---
title: Hata ayıklama görevleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4a8a9879bce6d91448bb4f29b842328ab56bb97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200605"
---
# <a name="debugging-tasks"></a>Hata Ayıklama Görevleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir programda hata ayıklamak için, başlatılmalıdır ve buna bir hata ayıklama altyapısı (DE) eklenmelidir, aksi takdirde DE daha önce başlatılmış bir programa eklenmelidir. İliştirildikten sonra, belirli başlangıç olaylarını üretmelidir. Yanıt olarak, hata ayıklama paketi IDE 'de ayarlanan kesme noktalarını bağlamaya çalışır. Program, bağlantılı bir kesme noktasına rastarsa, durdurur ve Kullanıcı girişini bekler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Güvenlik sorunları](../../extensibility/debugger/security-issues.md)  
 Bir programın hatalarını ayıklamak için gereken güvenlik adımlarını açıklar.  
  
 [Program Başlatma](../../extensibility/debugger/launching-a-program.md)  
 Programı başlatmak için işletim sistemini çağıran bir DE belirtme hakkında adım adım yönergeler sağlar.  
  
 [Doğrudan Programa Ekleme](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Zaten çalışmakta olan bir işlemdeki programda hata ayıklamak için kullanılan süreci açıklar.  
  
 [Başlatmadan Sonra Başlangıç Olaylarını Gönderme](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Program ana giriş noktasına gelene ve hata ayıklama için hazırlanana kadar,, programa eklendikten sonra gerçekleşmekte olan olayları listeler.  
  
 [Yürütme Denetimi](../../extensibility/debugger/control-of-execution.md)  
 , Koşullara bağlı olarak genellikle bir giriş noktası olayını, yük-tam olayı veya durdurma olayını nasıl göndereceğini açıklar.  
  
 [Kesme Noktaları Bağlama](../../extensibility/debugger/binding-breakpoints.md)  
 Kullanıcı bir kesme noktası ayarladıysanız, IDE 'nin isteği nasıl oluşturup hata ayıklama oturumunda kesme noktası oluşturmasını isteyip isteyebileceğinizi açıklar.  
  
 [İfadeleri Değerlendirme](../../extensibility/debugger/evaluating-expressions.md)  
 İfadelerin nasıl oluşturulduğunu ve bir ifadenin değerlendirildiği zaman ne olacağını açıklar.  
  
 [Verileri Görselleştirme ve Görüntüleme](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Tür görselleştiricilerinin ve özel görüntüleyicilerin ifade değerlendirici (EE) tarafından nasıl desteklendiği açıklanmaktadır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklayıcı Kavramları](../../extensibility/debugger/debugger-concepts.md)  
 Ana hata ayıklama mimarisi kavramlarını açıklar.  
  
 [Hata Ayıklayıcı Bileşenleri](../../extensibility/debugger/debugger-components.md)  
 Visual Studio hata ayıklama bileşenlerine genel bir bakış sağlar. Bu, DE, EE ve symbol işleyicisini (SH) içerir.  
  
 [Hata Ayıklayıcı Bağlamları](../../extensibility/debugger/debugger-contexts.md)  
 Aynı anda kod, belge ve ifade değerlendirme bağlamlarının içinde nasıl çalıştığını açıklar. Üç bağlamın her biri için, bu konuyla ilgili konum, konum veya değerlendirmeyi açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
