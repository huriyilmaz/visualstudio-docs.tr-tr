---
title: Düzenle ve Devam (Visual Basic) | Microsoft Docs
description: Düzenle ve Devam' Visual Basic kullanılabilir. Hangi düzenlemelerin desteklen olduğunu ve düzenlemelerin uygulanıp uygulanmaycalarını denetlemeyi öğrenin.
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
ms.openlocfilehash: 9c02eacca6661a846ab387dd1ec9199aa1d41fd0624c91e5f828f176f230283c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391516"
---
# <a name="edit-and-continue-visual-basic"></a>Düzenle ve Devam Et (Visual Basic)
Düzenle ve Devam Bırak, kesme modunda yürüten kodunuzu [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] değiştirmenizi sağlayan bir hata ayıklama özelliğidir. Kod düzenlemeleri uygulandıktan sonra, yeni düzenlemelerle kod yürütmeyi sürdürebilirsiniz ve bu etkiyi görüyorsunuz.

 Kesme moduna her girişte Düzenle ve Devam Edin özelliğini kullanabilirsiniz. Kesme modunda, kaynak pencerede sarı bir ok ucu olan yönerge işaretçisi, bir yöntem veya özellik gövdesinde yürütülebilir deyim içeren satıra işaret ediyor ve daha sonra yürütülecek.

 Düzenle ve Devam Değiştir, hata ayıklama oturumu sırasında yapmak istediğiniz değişikliklerin çoğunu destekler, ancak bazı özel durumlar vardır. Daha fazla bilgi için [bkz. Desteklenen Kod Değişiklikleri (C# ve Visual Basic).](../debugger/supported-code-changes-csharp.md)

 Yetkisiz bir düzenleme oraya geldiğinde, değişiklik mor dalgalı alt çizgiyle işaretlenir ve bu alt çizgide bir Görev Listesi. Düzenle ve Devam'a devam etmek için yetkisiz bir düzenlemeyi geri al gerekir. Düzenle ve Devam'ın dışında yapılırsa bazı yetkisiz düzenlemelere izin verilir. Böyle yetkisiz bir düzenlemenin sonuçlarını korumak için hata ayıklamayı durdurmanız ve uygulamanızı yeniden başlatmanız gerekir.

 Düzenle ve Devam Edin, Windows 10 için UWP uygulamaları ve .NET Framework 4.6 masaüstü veya sonraki sürümlerini (.NET Framework yalnızca masaüstü sürümüdür) hedef alan x86 ve x64 uygulamaları için de kullanılabilir.

 > [!NOTE]
 > Desteklenmeyen uygulamalar ve platformlar arasında ASP.NET 5, Silverlight 5 ve Windows 8.1.

 İşleme Ekle'yi kullanarak hata ayıklamaya başlarken Düzenle ve Devam **Etmek desteklenmiyor.** İyileştirilmiş kod veya karma yönetilen ve yerel kod için Düzenle ve Devam Etmek desteklenmiyor. Daha fazla bilgi için [bkz. Desteklenen Kod Değişiklikleri (C# ve Visual Basic).](../debugger/supported-code-changes-csharp.md)

 Bu bölümdeki konular, bu özelliğin nasıl ve hangi tür değişikliklere izin verilmiyor hakkında ek ayrıntılar sağlar.

## <a name="in-this-section"></a>Bu Bölümde
 [Nasıl yapılır: Düzenle ve Devam Ile Kesme Modunda Düzenleme Uygulama](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md) Kesme modunda kod düzenlemelerini uygulama hakkında açıklama.

 [Desteklenen Kod Değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md) Düzenle ve Devam'da gerçekleştirilecek düzenleme [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] türlerini açıklar.

## <a name="related-sections"></a>İlgili Bölümler
 [Düzenle ve Devam](../debugger/edit-and-continue.md) Düzenle ve Devam'da konu başlıklarının listesini sağlar.
