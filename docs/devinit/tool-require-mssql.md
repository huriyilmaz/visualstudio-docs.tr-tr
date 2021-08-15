---
title: require-mssql
description: devinit aracı-MSSQL gerektirir.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 7ad7e9d8518457c3f0c09164c0e1e9d561d229cea1afa59f72b1009a29324784
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390544"
---
# <a name="require-mssql"></a>require-mssql

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`require-mssql`araç, [Microsoft SQL Server 2019 Developer Edition](https://www.microsoft.com/sql-server/application-development) 'ı MS SQL Server ıso aracılığıyla yüklemek için kullanılır. SQL sunucusu, `localhost` tümleşik Windows kimlik doğrulaması kullanılarak kullanılabilir olacaktır SQL sunucusu bağlantı dizesiyle erişilebilir olacaktır `"Server=localhost;Integrated Security=true;"` .

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                   |
| [**girişinin**](#input)                              | dize | No       | Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                                                  |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.              |

### <a name="input"></a>Giriş

`input`Özelliği iki değerden birini içeren bir dize olabilir:

| Değer     | Açıklama                              |
|-----------|------------------------------------------|
| install   | SQL sunucusu yüklenir.                     |
| kaldırma | tüm SQL sunucu yüklemelerini kaldırır. |

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

aracın varsayılan davranışı `require-mssql` SQL sunucusu yüklemektir.

### <a name="built-in-options"></a>Yerleşik Seçenekler

`require-mssql`Araç, yükleyicinin gözetimsiz olarak çalıştırıladiğinden emin olmak için bir dizi yükleyici komut satırı bağımsız değişkeni ayarlar. bu bağımsız değişkenler aşağıda listelenmiştir ve bunlara ilişkin belgeler [SQL yüklemesi belgelerinde](/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15&preserve-view=true)bulunabilir.

| Ad                                                               | Açıklama |
|--------------------------------------------------------------------|-------------|
| /q                                                                 |             |
| /ACTION = Install                                                    |             |
| /FEATURES = SQLEngine, LocalDB                                       |             |
| /UpdateEnabled                                                     |             |
| /UpdateSource = MU                                                   |             |
| /X86 = yanlış                                                         |             |
| /ıNSTANCENAME = MSSQLSERVER                                          |             |
| /INSTALLSHAREDDIR = "C:\Program Files \ Microsoft SQL Server"          |             |
| /INSTALLSHAREDWOWDIR = "C:\Program Files (x86) \ Microsoft SQL Server" |             |
| /SQLSVCıNSTANTFILEINIT = true                                        |             |
| /INSTANCEDIR = "C:\Program Files \ Microsoft SQL Server"               |             |
| /AGTSVCACCOUNT = "NT Service\SQLSERVERAGENT"                         |             |
| /AGTSVCSTARTUPTYPE = Manual                                          |             |
| /SQLSVCSTARTUPTYPE = otomatik                                       |             |
| /SQLHARMANLAMA = "SQL_Latin1_General_CP1_CI_AS"                       |             |
| /SQLSVCACCOUNT = "NT Service\MSSQLSERVER"                            |             |
| /SQLSYSADMINACCOUNTS = Yöneticiler                                |             |
| /IACCEPTSQLSERVERLICENSETERMS                                      |             |

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren bir örnek aşağıda verilmiştir `require-msssql` `.devinit.json` .

#### <a name="devinitjson-that-will-install-mssql"></a>.devinit.js, MSSQL 'yi yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-mssql",
            "input": "install",
        }
    ]
}
```