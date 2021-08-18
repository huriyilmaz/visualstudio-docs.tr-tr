---
title: Testsettings 'ı runsettings 'e geçirin
description: Testsettings 'ı runsettings 'e geçirmeyi öğrenin
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047328"
---
# <a name="upgrade-from--testsettings-to-runsettings"></a>*. Testsettings* 'den *. runsettings* 'e yükselt

Test yapılandırma dosyanızı. *testsettings* ' den *. runsettings* ' den, Visual Studio birlikte yükleyen SettingsMigrator aracıyla yükseltebilirsiniz. Visual Studio yüklemesinin konumuna bağlı olarak, aşağıdaki yolda settings migrator aracını bulabilirsiniz:`C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`

Doğru dizin konumunda, aracı aşağıdaki biçimde çalıştırabilirsiniz:

```console
SettingsMigrator.exe <Full path to testsettings file to be migrated>
SettingsMigrator.exe <Full path to testsettings file to be migrated> <Full path to runsettings file to be created>
```

## <a name="examples"></a>Örnekler
```console
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings E:\MyTest\MyNewRunSettings.runsettings
```

*. Testsettings* seçeneklerinin *. runsettings* ' e nasıl dönüştürüleceği hakkında daha fazla bilgi almak istiyorsanız, GitHub üzerindeki [açık kaynak test platformu deposunda](https://github.com/microsoft/vstest-docs/blob/master/RFCs/0023-TestSettings-Deprecation.md#migration) daha fazla uygulama ayrıntısı bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [İle test çalıştırmalarını yapılandırma `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [MSTestv1 'den MSTestv2 'ye yükseltme](../test/mstest-update-to-mstestv2.md)
- [Kodunuzun birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testlerinde hata ayıklama](../test/debug-unit-tests-with-test-explorer.md)
