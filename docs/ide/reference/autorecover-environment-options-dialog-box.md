---
title: AutoRecover, Ortam, Seçenekler İletişim Kutusu
description: Otomatik kurtarma, ortam, Seçenekler iletişim kutusu ve dosyaların otomatik olarak yedeklenip yedeklenmeyeceğini belirtmek için nasıl kullanıldığı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 08/14/2020
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9a90198ce4cf3dc54eedbf80bbf4ffbad634cbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836494"
---
# <a name="autorecover-environment-options-dialog-box"></a>Otomatik kurtarma, ortam, Seçenekler iletişim kutusu

Dosyaların otomatik olarak yedeklenip yedeklenmeyeceğini belirtmek için **Seçenekler** iletişim kutusunda bu sayfayı kullanın. Ayrıca, Visual Studio beklenmedik şekilde kapatılırsa değiştirilen dosyaları geri yüklemek istediğinizi de belirtebilirsiniz.

Bu iletişim kutusuna erişmek için **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Otomatik Kurtarma**' ya gidin.

:::image type="content" source="media/autorecover-options.png" alt-text="Seçenekler iletişim kutusundaki otomatik kurtarma bölümünün ekran görüntüsü":::

**Otomatik Kurtarma bilgilerini her [n] dakikada bir Kaydet**

::: moniker range="vs-2019"

Bir dosyanın düzenleyicide ne sıklıkta otomatik olarak kaydedileceğini özelleştirmek için bu seçeneği kullanın. Daha önce kaydedilen dosyalar için, Visual Studio 2019 sürüm 16,2 ve üzeri, dosyanın bir kopyasını ***%LocalAppData%\microsoft\visualstudio\backupfiles \\ [ProjectName]*** dizinine kaydeder. Dosya yeni ise ve henüz kaydetmediyseniz, Visual Studio otomatik olarak rastgele oluşturulmuş bir dosya adı kullanarak kaydeder.

> [!NOTE]
> Visual Studio 2019 sürüm 16,1 veya önceki bir sürümü kullanıyorsanız, dosya konumu *%userprofile%\, \Backup Files \\ [ProjectName]* olur. Daha fazla bilgi için [Visual Studio 2019 sürüm notları geçmişi](/visualstudio/releases/2019/release-notes-history/) sayfasına bakın.

::: moniker-end

::: moniker range="vs-2017"

Bir dosyanın düzenleyicide ne sıklıkta otomatik olarak kaydedileceğini özelleştirmek için bu seçeneği kullanın. Daha önce kaydedilen dosyalar için, Visual Studio 2017 dosyanın bir kopyasını *%userprofile%\, Studio [Version] \Backup Files \\ [ProjectName]* içinde kaydeder. Dosya yeni ise ve henüz kaydetmediyseniz, Visual Studio otomatik olarak rastgele oluşturulmuş bir dosya adı kullanarak kaydeder.

::: moniker-end

**[N] gün için otomatik kurtarma bilgilerini tut**

Visual Studio 'Nun otomatik kurtarma için oluşturulan dosyaları ne kadar süre tutacağını belirtmek için bu seçeneği kullanın.

### <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler iletişim kutusu](../../ide/reference/options-dialog-box-visual-studio.md)
