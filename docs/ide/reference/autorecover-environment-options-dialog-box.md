---
title: AutoRecover, Ortam, Seçenekler İletişim Kutusu
description: AutoRecover, Ortam, Seçenekler iletişim kutusu ve dosyaların otomatik olarak mı yoksa otomatik olarak mı silinip silinemezseniz nasıl kullanılır hakkında bilgi edinmek için bu iletişim kutusunu seçin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f3cdde0c409dfddbfb4468cbf7a6203260a42223
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101615"
---
# <a name="autorecover-environment-options-dialog-box"></a>AutoRecover, Ortam, Seçenekler iletişim kutusu

Dosyaları otomatik olarak mı yoksa **otomatik** olarak mı doğrulayacaklarını belirtmek için Seçenekler iletişim kutusunda bu sayfayı kullanın. Ayrıca, dosyanın beklenmedik şekilde kapanması Visual Studio geri yüklemek istediğiniz belirtebilirsiniz.

Bu iletişim kutusuna erişmek için Araçlar Seçenekler Ortam  >  **Otomatik**  >    >  **Kurtarma'ya gidin.**

:::image type="content" source="media/autorecover-options.png" alt-text="Seçenekler iletişim kutusundaki AutoRecover bölümünün ekran görüntüsü":::

**Her [n] dakikada bir AutoRecover bilgilerini kaydetme**

::: moniker range=">=vs-2022"

Bir dosyanın düzenleyicide otomatik olarak ne sıklıkta kaydedilebilir olduğunu özelleştirmek için bu seçeneği kullanın. Daha önce kaydedilen dosyalar Visual Studio dosyanın bir kopyasını ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles \\ [projectname] dizinine kaydeder.*** Dosya yeni ise ve henüz kaydedemediyebilirsiniz Visual Studio rastgele oluşturulan bir dosya adı kullanarak otomatik olarak otomatik olarak kodlar.

::: moniker-end

::: moniker range="vs-2019"

Bir dosyanın düzenleyicide otomatik olarak ne sıklıkta kaydedilebilir olduğunu özelleştirmek için bu seçeneği kullanın. Daha önce kaydedilen dosyalar için, Visual Studio 2019 sürüm 16.2 ve sonraki sürümler dosyanın bir kopyasını ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles \\ [projectname] dizinine kaydeder.*** Dosya yeni ise ve henüz kaydedemediyebilirsiniz Visual Studio rastgele oluşturulan bir dosya adı kullanarak otomatik olarak otomatik olarak kodlar.

> [!NOTE]
> Visual Studio 2019 sürüm 16.1 veya önceki bir sürümü kullanıyorsanız, dosya konumu *%USERPROFILE%\Documents\Visual Studio [version]\Backup Files \\ [projectname] konumundadır.* Daha fazla bilgi için Visual Studio [2019 Sürüm Notları Geçmişi sayfasına](/visualstudio/releases/2019/release-notes-history/) bakın.

::: moniker-end

::: moniker range="vs-2017"

Bir dosyanın düzenleyicide otomatik olarak ne sıklıkta kaydedilebilir olduğunu özelleştirmek için bu seçeneği kullanın. Daha önce kaydedilen dosyalar için Visual Studio 2017'de dosyanın bir kopyası *%USERPROFILE%\Documents\Visual Studio [version]\Backup Files \\ [projectname]* dizinine kaydedilir. Dosya yeni ise ve henüz kaydedemediyebilirsiniz Visual Studio rastgele oluşturulan bir dosya adı kullanarak otomatik olarak otomatik olarak kodlar.

::: moniker-end

**AutoRecover bilgilerini [n] gün boyunca tutma**

Otomatik kurtarma için dosyaların oluşturulma Visual Studio süre belirtmek için bu seçeneği kullanın.

### <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler iletişim kutusu](../../ide/reference/options-dialog-box-visual-studio.md)
