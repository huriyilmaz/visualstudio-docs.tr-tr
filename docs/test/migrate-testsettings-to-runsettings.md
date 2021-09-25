---
title: Testsetting'leri runsettings'e geçirme
description: Testsetting'leri runsetting'lere geçirmeyi öğrenin
ms.custom: SEO-VS-2020
ms.date: 03/18/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 348de2d34e30c96449dcd2e4c2ba6eb83ed24c4c
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429694"
---
# <a name="upgrade-from-testsettings-to-runsettings"></a>.testsettings'den .runsettings'e yükseltme

Test yapılandırma dosyanızı *,testsettings'den .runsettings'e* yükseltmek için, ayarlarla birlikte yüklemesi yapılan AyarlarMigrator Visual Studio.  Yükleme konumunuz Visual Studio bağlı olarak, ayarlar aracına aşağıdaki yolda bulabilirsiniz:
::: moniker range=">=vs-2022"
`C:\Program Files\Microsoft Visual Studio\2022\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`
::: moniker-end
::: moniker range="vs-2019"
`C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`
::: moniker-end

Doğru dizin konumda, aracı aşağıdaki biçimde çalıştırabilirsiniz:

```console
SettingsMigrator.exe <Full path to testsettings file to be migrated>
SettingsMigrator.exe <Full path to testsettings file to be migrated> <Full path to runsettings file to be created>
```

## <a name="examples"></a>Örnekler
```console
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings E:\MyTest\MyNewRunSettings.runsettings
```

*.testsettings seçeneklerinin .runsettings'e* nasıl dönüştürülmesiyle ilgili daha fazla bilgi için aşağıdaki açık kaynak [test platformu](https://github.com/microsoft/vstest-docs/blob/master/RFCs/0023-TestSettings-Deprecation.md#migration) deposunda daha fazla uygulama GitHub. 

## <a name="see-also"></a>Ayrıca bkz.

- [Test çalıştırmalarını ile yapılandırma `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [MSTestv1'den MSTestv2'ye yükseltme](../test/mstest-update-to-mstestv2.md)
- [Kodunuzu birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testlerinde hata ayıklama](../test/debug-unit-tests-with-test-explorer.md)
