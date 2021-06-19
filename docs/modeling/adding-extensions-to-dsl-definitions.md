---
title: DSL Tanımlarına Uzantılar Ekleme
description: DSL Tanımı uzantısının etki alanına özgü bir dile (DSL) yönelik bir uzantı paketi oluşturmanıza nasıl olanak tanıması olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d9f1c92ebb879517d497af41fe98cec4492bd95
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384895"
---
# <a name="add-extensions-to-dsl-definitions"></a>DSL Tanımlarına Uzantı Ekleme

DSL Tanımı uzantısı, etki alanına özgü bir dile (DSL) yönelik bir uzantı paketi oluşturmanıza olanak sağlar. Visual Studio Tümleştirme Uzantısı'nın (VSIX) içinde yer alan DSL uzantısı, bir kullanıcının bilgisayarına DSL ile aynı şekilde yükleyebilir. Ek özellikler çalışma zamanında dinamik olarak etkinleştirilebilir ve devre dışı bırakılabilir. DSL'lerin açıkça uzantı için tasarlanması gerekmez ve uzantılar daha sonra veya üçüncü taraflar tarafından genişletilmiş DSL değiştirilmeden tasarılabilir.

DSL uzantıları aşağıdaki özellikleri içerebilir:

- Model ve sunu öğelerinin özellikleri

- Şekiller ve bağlayıcılar için dekoratörler

- Sınıflar, ilişkiler, şekiller ve bağlayıcılar

- Doğrulama kısıtlamaları

- Araç kutusu öğeleri ve sekmeleri

Genişletilmiş DSL kullanıcısı, ek özelliklerin örneklerini içeren bir model oluşturabilir ve kaydedebilir. Model, uygun uzantıyı yüklemiş olan diğer kullanıcılar tarafından okunabilir. Uzantıyı yüklememiş kullanıcılar ek özellikleri kullanamaz, ancak ek özellikleri kaybetmeden modeli güncelleştire ve kaydedebilir.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [İlgili blog gönderileri](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
