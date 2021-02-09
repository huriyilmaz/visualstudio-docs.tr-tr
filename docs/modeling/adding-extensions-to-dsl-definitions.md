---
title: DSL Tanımlarına Uzantılar Ekleme
description: DSL tanımı uzantısının, etki alanına özgü dil (DSL) için Uzantı paketi oluşturmanıza nasıl olanak sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1208c152534206a0ed2894fc0e41d844e0b77d47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861965"
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
