---
title: require-mssql
description: devinit aracı-MSSQL gerektirir.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 2ad02a29b8ea8b59abd4f246c5cc1d206451d3fc
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005192"
---
# <a name="require-mssql"></a>require-mssql

`require-mssql`Araç, MS SQL Server ISO aracılığıyla [Microsoft SQL Server 2019 Developer Edition](https://www.microsoft.com/sql-server/application-development) 'ı yüklemek için kullanılır. SQL Server, `localhost` Tümleşik Windows kimlik doğrulaması kullanılarak kullanılabilir olacak ve SQL Server bağlantı dizesiyle erişilebilir olacaktır `"Server=localhost;Integrated Security=true;"` .

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                   |
| [**girişinin**](#input)                              | dize | No       | Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                                                  |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.              |

### <a name="input"></a>Giriş

`input`Özelliği iki değerden birini içeren bir dize olabilir:

| Değer     | Açıklama                              |
|-----------|------------------------------------------|
| install   | SQL Server 'ı kurar.                     |
| kaldırma | Tüm SQL Server yüklemelerini kaldırır. |

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `require-mssql` SQL Server 'ı yüklemektir.

### <a name="builtin-options"></a>Yerleşik Seçenekler

`require-mssql`Araç, yükleyicinin gözetimsiz olarak çalıştırıladiğinden emin olmak için bir dizi yükleyici komut satırı bağımsız değişkeni ayarlar. Bu bağımsız değişkenler aşağıda listelenmiştir ve bunlar üzerindeki belgeler [SQL yüklemesi belgelerinde](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15&preserve-view=true)bulunabilir.

| Ad                                                               | Açıklama |
|--------------------------------------------------------------------|-------------|
| /q                                                                 |             |
| /ACTION = Install                                                    |             |
| /FEATURES = SQLEngine, LocalDB                                       |             |
| /UpdateEnabled                                                     |             |
| /UpdateSource = MU                                                   |             |
| /X86 = yanlış                                                         |             |
| /ıNSTANCENAME = MSSQLSERVER                                          |             |
| /INSTALLSHAREDDIR = "C:\Program Files\Microsoft SQL Server"          |             |
| /INSTALLSHAREDWOWDIR = "C:\Program Files (x86) \Microsoft SQL Server" |             |
| /SQLSVCıNSTANTFILEINIT = true                                        |             |
| /INSTANCEDIR = "C:\Program Files\Microsoft SQL Server"               |             |
| /AGTSVCACCOUNT = "NT Service\SQLSERVERAGENT"                         |             |
| /AGTSVCSTARTUPTYPE = Manual                                          |             |
| /SQLSVCSTARTUPTYPE = otomatik                                       |             |
| /SQLHARMANLAMA = "SQL_Latin1_General_CP1_CI_AS"                       |             |
| /SQLSVCACCOUNT = "NT Service\MSSQLSERVER"                            |             |
| /SQLSYSADMINACCOUNTS = Yöneticiler                                |             |
| /IACCEPTSQLSERVERLICENSETERMS                                      |             |

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs MSSQL.",
            "tool": "require-mssql",
            "input": "install",
        }
    ]
}
```
