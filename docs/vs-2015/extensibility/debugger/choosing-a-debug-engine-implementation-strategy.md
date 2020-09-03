---
title: Hata ayıklama altyapısı uygulama stratejisi seçme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b03e69892da217d84d56b39b7df61784907d2b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183466"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Hata Ayıklama Altyapısı Uygulama Stratejisi Seçme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama altyapısı (DE) uygulama stratejinizi öğrenmek için çalışma zamanı mimarisini kullanın. Hata ayıklama altyapısı, hata ayıklaması yapılacak programa, Visual Studio oturumu hata ayıklama Yöneticisi 'ne (SDM) işlem içi veya her ikisine birden işlem dışı oluşturulmuş olabilir. Aşağıdaki kılavuzlar bu üç strateji arasından seçim yapmanıza yardımcı olmalıdır.  
  
## <a name="guidelines"></a>Yönergeler  
 Ayrıca, hem SDM 'nin hem de hata Ayıklanacak programın işlem dışı olması mümkün olsa da, genellikle bunu yapmanız gerekmez. İşlem sınırları genelinde çağrılar nispeten düşüktür.  
  
 Win32 yerel çalışma zamanı ortamı ve ortak dil çalışma zamanı ortamı için hata ayıklama motorları zaten sağlanmış. Bu ortamların her biri için DE ' yi değiştirmeniz gerekiyorsa, SDM ile de işlem içi oluşturmanız gerekir.  
  
 Aksi halde, hata ayıklama için işlem içi veya işlem içi işlemi oluşturma arasında, hataları Ayıklanacak programda oluşturma arasında seçim yapabilirsiniz. Ayrıca, öğesinin ifade değerlendiricisi tarafından program sembol deposuna sık erişim gerekip gerekmediğini ve sembol deposunun hızlı erişim için belleğe yüklenip yüklenmeyeceğini göz önünde bulundurmanız önemlidir. Ayrıca aşağıdakileri dikkate alın:  
  
- İfade değerlendiricisi ve sembol deposu arasında çok sayıda çağrı yoksa veya sembol deposu SDM bellek alanına okunıyorsa, SDM 'de DE işlem içi oluşturun. Hata ayıklama altyapısının CLSID 'sini programınıza iliştirdiğinden SDM 'ye döndürmelidir. SDM, bu CLSID 'in bir işlem içi örneğini oluşturmak için kullanır.  
  
- Sembol deposuna erişmek için DE programı çağırmanız gerekiyorsa, programla birlikte işlem içi oluşturun. Bu durumda program, DE örneğini oluşturur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
