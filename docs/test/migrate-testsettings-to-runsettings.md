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
ms.openlocfilehash: 749bb5e57770d76dfca69af40913d8d80c006679
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634222"
---
# <a name="upgrade-from--testsettings-to-runsettings"></a>*.testsettings'den* *.runsettings'e yükseltme*

Test yapılandırma *dosyanızı,.testsettings'den .runsettings'e* yükseltmek için, ayarlarla birlikte yüklü olan AyarlarMigrator Visual Studio.  Yükleme konumunuz Visual Studio bağlı olarak, ayarlar aracına aşağıdaki yolda bulabilirsiniz:`C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`

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

*.testsettings seçeneklerinin* *.runsettings'e* nasıl dönüştürülmesi hakkında daha fazla bilgi için aşağıdaki açık kaynak [test platformu](https://github.com/microsoft/vstest-docs/blob/master/RFCs/0023-TestSettings-Deprecation.md#migration) deposunda daha fazla uygulama GitHub.

## <a name="see-also"></a>Ayrıca bkz.

- [Test çalıştırmalarını ile yapılandırma `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [MSTestv1'den MSTestv2'ye yükseltme](../test/mstest-update-to-mstestv2.md)
- [Kodunuzu birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testlerinde hata ayıklama](../test/debug-unit-tests-with-test-explorer.md)
