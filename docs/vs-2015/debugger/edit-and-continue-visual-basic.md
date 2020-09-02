---
title: Düzenle ve devam et (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 43
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24782fee98cff09513ff2b4d1606f2be0bd9fbd2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428561"
---
# <a name="edit-and-continue-visual-basic"></a>Düzenle ve Devam Et (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenle ve devam et, hata ayıklama için bir özelliktir ve [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Bu, kesme modunda yürütülürken kodunuzu değiştirmenize olanak sağlar. Kod düzenlemeleri uygulandıktan sonra, yeni düzenlemelerle birlikte kod yürütmeyi sürdürmeye ve etkiyi görmenizi sağlayabilirsiniz.  
  
 Kesme moduna girerken Düzenle ve devam et özelliğini kullanabilirsiniz. Kesme modunda, yönerge işaretçisi, kaynak penceredeki sarı bir ok ucu, bir sonraki çalıştırılacak satıra işaret eder ve bir yöntem veya Özellik gövdesi içindeki yürütülebilir bir bildirimde bulunur. Kesme modundayken çalıştırılabilir deyimlerde neredeyse her türlü değişikliği yapabilirsiniz ve değişiklik temel alınan projeye dahil edilir. Ancak kesme modundayken, genel yöntemler, ortak alanlar veya sınıf bildirimleri gibi bildirim deyimlerini genellikle değiştirmenize izin verilmez.  
  
 Yetkisiz bir düzenleme yaptığınızda, değişiklik mor dalgalı alt çizgiyle işaretlenir ve Görev Listesi bir görev görüntülenir. Düzenle ve devam et ' i kullanmaya devam etmek istiyorsanız yetkisiz düzenlemeyi geri almalısınız. Düzenle ve devam et dışında yapıldığında, bazı yetkisiz düzenlemelere izin verilir. Böyle bir yetkisiz düzenleme sonuçlarını sürdürmek istiyorsanız, hata ayıklamayı durdurup uygulamanızı yeniden başlatmanız gerekir.  
  
 Düzenle ve devam et, .NET Framework 4.5.1 ' i hedefleyen 64-bit projeler için desteklenir.  
  
 **Işleme İliştir**kullanarak hata ayıklamaya başladığınızda Düzenle ve devam et desteklenmez. En iyi duruma getirilmiş kod, karma yönetilen ve yerel kod veya Compact Framework (akıllı cihaz) projeleri için Düzenle ve devam et desteklenmez.  
  
 Bu bölümdeki konularda, bu özelliğin nasıl kullanılacağı ve ne tür değişikliklere izin verilmediğinden ilgili ek ayrıntılar sağlanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl Yapılır: Düzenle ve Devam Et ile Kesme Modunda Düzenlemeleri Uygulama](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Kesme modunda kod düzenlemelerinin nasıl uygulanacağını açıklar.  
  
 [Visual Basic Düzenle ve Devam Et'de Desteklenmeyen Düzenlemeler](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 Düzenle ve devam et 'de hangi düzenleme türlerinin gerçekleştirilebileceğini açıklar [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] .  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Düzenle ve Devam Et](../debugger/edit-and-continue.md)  
 Düzenle ve devam et ile ilgili konuların bir listesini sağlar.
