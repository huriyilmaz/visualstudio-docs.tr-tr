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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: af89cfb0e47655e5deac867e5eeec1da255408c27d6037468ad8e42f8fe31c8a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400262"
---
# <a name="autorecover-environment-options-dialog-box"></a>Otomatik kurtarma, ortam, Seçenekler iletişim kutusu

Dosyaların otomatik olarak yedeklenip yedeklenmeyeceğini belirtmek için **Seçenekler** iletişim kutusunda bu sayfayı kullanın. ayrıca, Visual Studio beklenmedik şekilde kapatılırsa değiştirilen dosyaları geri yüklemek istediğinizi de belirtebilirsiniz.

Bu iletişim kutusuna erişmek için **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Otomatik Kurtarma**' ya gidin.

:::image type="content" source="media/autorecover-options.png" alt-text="Seçenekler iletişim kutusundaki otomatik kurtarma bölümünün ekran görüntüsü":::

**Otomatik Kurtarma bilgilerini her [n] dakikada bir Kaydet**

::: moniker range=">=vs-2022"

Bir dosyanın düzenleyicide ne sıklıkta otomatik olarak kaydedileceğini özelleştirmek için bu seçeneği kullanın. daha önce kaydedilen dosyalar için, Visual Studio dosyanın bir kopyasını ***%localappdata%\microsoft\visualstudio\backupfiles \\ [projectname]*** dizinine kaydeder. dosya yeni ise ve henüz kaydetmediyseniz, Visual Studio otomatik olarak, rastgele oluşturulmuş bir dosya adı kullanarak kaydeder.

::: moniker-end

::: moniker range="vs-2019"

Bir dosyanın düzenleyicide ne sıklıkta otomatik olarak kaydedileceğini özelleştirmek için bu seçeneği kullanın. daha önce kaydedilen dosyalar için, Visual Studio 2019 sürüm 16,2 ve üzeri, dosyanın bir kopyasını ***%localappdata%\microsoft\visualstudio\backupfiles \\ [projectname]*** dizinine kaydeder. dosya yeni ise ve henüz kaydetmediyseniz, Visual Studio otomatik olarak, rastgele oluşturulmuş bir dosya adı kullanarak kaydeder.

> [!NOTE]
> Visual Studio 2019 sürüm 16,1 veya önceki bir sürümü kullanıyorsanız, dosya konumu *%userprofile%\documents\ Visual Studio [version] \Backup Files \\ [projectname]* olur. daha fazla bilgi için [Visual Studio 2019 sürüm notları geçmişi](/visualstudio/releases/2019/release-notes-history/) sayfasına bakın.

::: moniker-end

::: moniker range="vs-2017"

Bir dosyanın düzenleyicide ne sıklıkta otomatik olarak kaydedileceğini özelleştirmek için bu seçeneği kullanın. daha önce kaydedilen dosyalar için Visual Studio 2017, dosyanın bir kopyasını *%userprofile%\documents\ Visual Studio [version] \Backup files \\ [projectname]* içinde kaydeder. dosya yeni ise ve henüz kaydetmediyseniz, Visual Studio otomatik olarak, rastgele oluşturulmuş bir dosya adı kullanarak kaydeder.

::: moniker-end

**[N] gün için otomatik kurtarma bilgilerini tut**

Visual Studio, otomatik kurtarma için oluşturulan dosyaları ne kadar süreyle tutacağını belirtmek için bu seçeneği kullanın.

### <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler iletişim kutusu](../../ide/reference/options-dialog-box-visual-studio.md)
