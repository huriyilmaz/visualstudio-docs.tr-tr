---
title: Düzenle ve devam et (Visual Basic) | Microsoft Docs
description: düzenle ve devam et Visual Basic projeleri için kullanılabilir. Hangi düzenlemelerin desteklendiğini ve düzenlemelerinizin ne zaman uygulandığını nasıl denetleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a0d4206dba5991ccebd2747370c5143430cfd73e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030993"
---
# <a name="edit-and-continue-visual-basic"></a>Düzenle ve Devam Et (Visual Basic)
Düzenle ve devam et, hata ayıklama için bir özelliktir ve [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] Bu, kesme modunda yürütülürken kodunuzu değiştirmenize olanak sağlar. Kod düzenlemeleri uygulandıktan sonra, yeni düzenlemelerle birlikte kod yürütmeyi sürdürmeye ve etkiyi görmenizi sağlayabilirsiniz.

 Kesme moduna girerken Düzenle ve devam et özelliğini kullanabilirsiniz. Kesme modunda, kaynak penceredeki sarı bir ok ucu olan yönerge işaretçisi, bir sonraki çalıştırılacak yöntem veya özellik gövdesinde yürütülebilir bir ifade içeren çizgiyi işaret eder.

 Düzenle ve devam et, hata ayıklama oturumu sırasında yapmak isteyebileceğiniz birçok değişikliği destekler, ancak bazı özel durumlar vardır. Daha fazla bilgi için bkz. [desteklenen kod değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Yetkisiz bir düzenleme yaptığınızda, değişiklik mor dalgalı alt çizgiyle işaretlenir ve Görev Listesi bir görev görüntülenir. Düzenle ve devam et ' i kullanmaya devam etmek istiyorsanız yetkisiz düzenlemeyi geri almalısınız. Düzenle ve devam et dışında yapıldığında, bazı yetkisiz düzenlemelere izin verilir. Böyle bir yetkisiz düzenleme sonuçlarını sürdürmek istiyorsanız, hata ayıklamayı durdurup uygulamanızı yeniden başlatmanız gerekir.

 düzenle ve devam et, Windows 10 için UWP uygulamalarında ve .NET Framework 4,6 masaüstü veya sonraki sürümlerini hedefleyen x86 ve x64 uygulamaları (.NET Framework yalnızca bir masaüstü sürümüdür) ile desteklenir.

 > [!NOTE]
 > desteklenmeyen uygulamalar ve platformlar ASP.NET 5, Silverlight 5 ve Windows 8.1 içerir.

 **Işleme İliştir** kullanarak hata ayıklamaya başladığınızda Düzenle ve devam et desteklenmez. En iyileştirilmiş kod veya karma yönetilen ve yerel kod için Düzenle ve devam et desteklenmez. Daha fazla bilgi için bkz. [desteklenen kod değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Bu bölümdeki konularda, bu özelliğin nasıl kullanılacağı ve ne tür değişikliklere izin verilmediğinden ilgili ek ayrıntılar sağlanmaktadır.

## <a name="in-this-section"></a>Bu Bölümde
 [Nasıl yapılır: Düzenle ve devam et Ile kesme modunda düzenleme uygulama](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md) Kesme modunda kod düzenlemelerinin nasıl uygulanacağını açıklar.

 [Desteklenen kod değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md) Düzenle ve devam et 'de hangi düzenleme türlerinin gerçekleştirilebileceğini açıklar [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] .

## <a name="related-sections"></a>İlgili Bölümler
 [Düzenle ve devam et](../debugger/edit-and-continue.md) Düzenle ve devam et ile ilgili konuların bir listesini sağlar.
