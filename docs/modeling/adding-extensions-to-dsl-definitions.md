---
title: DSL Tanımlarına Uzantılar Ekleme
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2500fc8d9e09d95d7972a4b151b01937a5570a08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544241"
---
# <a name="add-extensions-to-dsl-definitions"></a>DSL Tanımlarına Uzantı Ekleme

DSL tanımı uzantısı, etki alanına özgü dil (DSL) için Uzantı paketi oluşturmanıza olanak sağlar. Bir Visual Studio Tümleştirme Uzantısı 'nda (VSıX) bulunan DSL uzantısı, bir kullanıcının bilgisayarına DSL ile aynı şekilde yüklenebilir. Ek özellikler dinamik olarak etkinleştirilebilir ve çalışma zamanında devre dışı bırakılabilir. DSLs 'in uzantı için açıkça tasarlanmaları gerekmez ve uzantılar, genişletilmiş DSL 'yi değiştirmeksizin daha sonra veya üçüncü taraflarca tasarlanabilir.

DSL uzantıları aşağıdaki özellikleri içerebilir:

- Model ve sunum öğelerinin özellikleri

- Şekiller ve bağlayıcılar için dekoratörler

- Sınıflar, ilişkiler, şekiller ve bağlayıcılar

- Doğrulama kısıtlamaları

- Araç kutusu öğeleri ve sekmeleri

Genişletilmiş bir DSL kullanıcısı ek özelliklerin örneklerini içeren bir model oluşturabilir ve kaydedebilir. Model, uygun uzantıyı yüklemiş olan diğer kullanıcılar tarafından okunabilir. Uzantıyı yüklememiş kullanıcılar ek özellikleri kullanamaz, ancak ek özellikleri kaybetmeden bir modeli güncelleştirebilir ve kaydedebilir.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [İlgili blog gönderileri](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
