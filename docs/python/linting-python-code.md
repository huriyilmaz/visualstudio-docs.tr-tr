---
title: Python kodu için PyLint kullanma
description: eklentileri özelleştirmek için komut satırı seçenekleri de dahil olmak üzere Python kodundaki sorunları denetlemek için Visual Studio pylint ' i çalıştırın.
ms.date: 03/13/2019
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 101c9614af4a78a7e2b4f3037e1e93d9b388786f
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972199"
---
# <a name="use-pylint-to-check-python-code"></a>Python kodunu denetlemek için PyLint kullanın

, python kodundaki hataları denetleyen ve iyi python kodlama düzenlerini etkileyen, yaygın olarak kullanılan bir araç olan [pylint](https://www.pylint.org/), python projeleri için Visual Studio tümleşiktir.

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

Pylınt belgelerinin [komut satırı seçenekleri](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) bölümü, bir *. pylintrc* yapılandırma dosyası aracılığıyla pylınt 'nin davranışının nasıl kontrol edileceğini açıklar. bu tür bir dosya, bu ayarların ne kadar büyük bir yere uygulanacağını (ayrıntılar için [komut satırı seçeneklerine](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) bakın) göre Visual Studio veya başka bir konumda bir Python projesinin köküne yerleştirilebilir.

Örneğin, bir projede *. pylintrc* dosyası ile önceki görüntüde gösterilen "docstring" uyarılarını gizlemek için şu adımları uygulayın:

1. Komut satırında, proje köküne gidin ( *. pyproj* dosyanız) ve açıklamalı bir yapılandırma dosyası oluşturmak için aşağıdaki komutu çalıştırın:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. Visual Studio Çözüm Gezgini, projenize sağ tıklayın,   >  **var olan öğe** ekle ' yi seçin, yeni *. pylintrc* dosyasına gidin, seçin ve **ekle**' yi seçin.

1. Üzerinde çalıştığınız çeşitli ayarlara sahip olan dosyayı düzenlenmek üzere açın. Bir uyarıyı devre dışı bırakmak için `[MESSAGES CONTROL]` bölümünü bulun, ardından `disable` Bu bölümdeki ayarı bulun. İstediğiniz uyarıları ekleyebileceğiniz belirli iletiler için uzun bir dize vardır. Buradaki örnekte, Append `,missing-docstring` (virgülle ayırıcı dahil).

1. *. Pylintrc* dosyasını kaydedin ve uyarıların artık bastırıldığına bakmak Için PyLint ' i yeniden çalıştırın.

> [!Tip]
> Bir ağ paylaşımından *. pylintrc* dosyasını kullanmak IÇIN, `PYLINTRC` UNC yolu veya eşleştirilmiş bir sürücü harfi kullanarak ağ paylaşımındaki dosya adının değeriyle adlı bir ortam değişkeni oluşturun. Örneğin, `PYLINTRC=\\myshare\python\.pylintrc`.
