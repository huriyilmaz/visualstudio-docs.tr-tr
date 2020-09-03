---
title: Bir programın ayıklanamayacağını etkinleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0f0331430a1cc625dee2a7029742fd62d67fb56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155370"
---
# <a name="enabling-a-program-to-be-debugged"></a>Bir Programı Hataları Ayıklanacak Şekilde Etkinleştirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama altyapısından (DE) bir programda hata ayıklamadan önce, önce bunu başlatmanız veya mevcut bir programa bağlamanız gerekir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bağlantı Noktası Alma](../../extensibility/debugger/getting-a-port.md)  
 Bir programın ayıklanamayacağını etkinleştirmeye yönelik ilk adım olarak bir bağlantı noktasının nasıl alınacağını açıklar.  
  
 [Program Kaydetme](../../extensibility/debugger/registering-the-program.md)  
 Bir programın hata ayıklamanın nasıl giderileceği konusunda bir sonraki adımı açıklar: bağlantı noktası ile kaydediliyor. Kaydolduktan sonra programa ekleme veya tam zamanında (JıT) hata ayıklama işlemi tarafından hata ayıklanabilir.  
  
 [Programa Ekleme](../../extensibility/debugger/attaching-to-the-program.md)  
 Bir sonraki adımı açıklar: hata ayıklayıcıyı programa ekleme.  
  
 [Başlatma tabanlı Iliştirme](../../extensibility/debugger/launch-based-attachment.md)  
 , SDM tarafından başlatma sonrasında otomatik olan bir programa başlatma tabanlı ek açıklar.  
  
 [Gerekli Olayları Gönderme](../../extensibility/debugger/sending-the-required-events.md)  
 Bir hata ayıklama altyapısı (DE) oluştururken ve bir programa iliştirirken gerekli olaylarda adım adım ilerleyin.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Özel Hata Ayıklama Altyapısı Oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Bir hata ayıklama altyapısı (DE) tanımlar ve ayrıca, bu arabirimler aracılığıyla uygulanan Hizmetleri ve hata ayıklayıcının farklı çalışma modları arasında geçişine neden olabilecekleri hizmetleri açıklar.
