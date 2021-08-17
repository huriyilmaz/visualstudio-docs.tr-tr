---
title: require-mssql
description: devinit tool require-mssql.
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
> 12 Nisan 2021'den itibaren Visual Studio 2019'dan GitHub Codespaces'a bağlanma desteklemeyecek ve bu özel önizleme sonuçlandırıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

Araç, `require-mssql` MS SQL server ISO üzerinden Microsoft SQL Server [2019 Developer Edition'ı](https://www.microsoft.com/sql-server/application-development) yüklemek için kullanılır. SQL sunucusu, tümleşik kimlik doğrulaması Windows üzerinde kullanılabilir SQL sunucusuna `localhost` bağlantı dizesiyle erişilebilir. `"Server=localhost;Integrated Security=true;"`

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak [açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli | Değer                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                                   |
| [**Giriş**](#input)                              | dize | No       | Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın.                                                  |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. Ayrıntılar [için aşağıdaki](#additional-options) Ek seçenekler'e bakın.              |

### <a name="input"></a>Giriş

özelliği `input` iki değerden birini içeren bir dize olabilir:

| Değer     | Açıklama                              |
|-----------|------------------------------------------|
| install   | Bir SQL yüklenir.                     |
| Kaldırmak | Tüm sunucu SQL kaldırır. |

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan `require-mssql` davranışı, SQL yüklemektir.

### <a name="built-in-options"></a>Yerleşik seçenekler

Araç, `require-mssql` yükleyicinin başsız çalışması için bir dizi yükleyici komut satırı bağımsız değişkeni ayarlar. Bu bağımsız değişkenler aşağıda listelenmiştir ve bu bağımsız değişkenlerle ilgili belgeler yükleme [SQL bulunabilir.](/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15&preserve-view=true)

| Ad                                                               | Açıklama |
|--------------------------------------------------------------------|-------------|
| /q                                                                 |             |
| /ACTION=Yükle                                                    |             |
| /FEATURES=SQLEngine, LocalDB                                       |             |
| /UpdateEnabled                                                     |             |
| /UpdateSource=MU                                                   |             |
| /X86=false                                                         |             |
| /INSTANCENAME=MSSQLSERVER                                          |             |
| /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server"          |             |
| /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" |             |
| /SQLSVCINSTANTFILEINIT=True                                        |             |
| /INSTANCEDIR="C:\Program Files\Microsoft SQL Server"               |             |
| /AGTSVCACCOUNT="NT Service\SQLSERVERAGENT"                         |             |
| /AGTSVCSTARTUPTYPE=Manual                                          |             |
| /SQLSVCSTARTUPTYPE=Automatic                                       |             |
| /SQLCOLLATION="SQL_Latin1_General_CP1_CI_AS"                       |             |
| /SQLSVCACCOUNT="NT Service\MSSQLSERVER"                            |             |
| /SQLSYSADMINACCOUNTS=Administrators                                |             |
| /IACCEPTSQLSERVERLICENSETERMS                                      |             |

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırmaya bir `require-msssql` örnek `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-install-mssql"></a>.devinit.jsMSSQL'i yüklemesi için:
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