---
title: Python kodu için PyLint kullanma
description: Python kodundaki sorunları denetlemek için komut satırı seçenekleri de dahil olmak üzere Visual Studio 'da Pylınt komutunu çalıştırın.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d410fd7575b6f71f272f6924d15249f89aa6ebcc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540107"
---
# <a name="use-pylint-to-check-python-code"></a>Python kodunu denetlemek için PyLint kullanın

[Pylint](https://www.pylint.org/), Python kodundaki hataları denetleyen ve iyi Python kodlama düzenlerini etkileyen yaygın olarak kullanılan bir araçtır. Bu, Python projeleri Için Visual Studio ile tümleşiktir.

## <a name="run-pylint"></a>PyLint Çalıştır

**Çözüm Gezgini** bir Python projesine sağ tıkladıktan sonra **Python**  >  **Run pylint**' i seçmeniz yeterlidir:

![Python projeleri için bağlam menüsünde Pylınt komutu](media/code-pylint-command.png)

Bu komutun kullanılması, zaten mevcut değilse, etkin ortamınıza PyLint 'i yüklemenizi ister.

Pylınt uyarıları ve hataları **hata listesi** penceresinde görüntülenir:

![Pylınt hata listesi](media/code-pylint-error-list.png)

Bir hataya çift tıklamak sizi sorunu oluşturan kaynak koda doğrudan götürür.

> [!Tip]
> Tüm Pylınt çıkış iletilerinin ayrıntılı bir listesi için bkz. [pylınt Özellikler başvurusu](https://pylint.readthedocs.io/en/latest/technical_reference/features.html) .

## <a name="set-pylint-command-line-options"></a>Pylınt komut satırı seçeneklerini ayarla

Pylınt belgelerinin [komut satırı seçenekleri](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) bölümü, bir *. pylintrc* yapılandırma dosyası aracılığıyla pylınt 'nin davranışının nasıl kontrol edileceğini açıklar. Bu tür bir dosya, Visual Studio 'daki bir Python projesinin köküne yerleştirilebilir ve bu ayarların ne kadar büyük bir yere uygulanacağını (Ayrıntılar için bkz. [komut satırı seçeneklerine](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) bakın).

Örneğin, bir projede *. pylintrc* dosyası ile önceki görüntüde gösterilen "docstring" uyarılarını gizlemek için şu adımları uygulayın:

1. Komut satırında, proje köküne gidin ( *. pyproj* dosyanız) ve açıklamalı bir yapılandırma dosyası oluşturmak için aşağıdaki komutu çalıştırın:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. Visual Studio Çözüm Gezgini, projenize sağ tıklayın, **Add**  >  **var olan öğe**Ekle ' yi seçin, yeni *. pylintrc* dosyasına gidin, seçin ve **Ekle**' yi seçin.

1. Üzerinde çalıştığınız çeşitli ayarlara sahip olan dosyayı düzenlenmek üzere açın. Bir uyarıyı devre dışı bırakmak için `[MESSAGES CONTROL]` bölümünü bulun, ardından `disable` Bu bölümdeki ayarı bulun. İstediğiniz uyarıları ekleyebileceğiniz belirli iletiler için uzun bir dize vardır. Buradaki örnekte, Append `,missing-docstring` (virgülle ayırıcı dahil).

1. *. Pylintrc* dosyasını kaydedin ve uyarıların artık bastırıldığına bakmak Için PyLint ' i yeniden çalıştırın.

> [!Tip]
> Bir ağ paylaşımından *. pylintrc* dosyasını kullanmak IÇIN, `PYLINTRC` UNC yolu veya eşleştirilmiş bir sürücü harfi kullanarak ağ paylaşımındaki dosya adının değeriyle adlı bir ortam değişkeni oluşturun. Örneğin, `PYLINTRC=\\myshare\python\.pylintrc`.
