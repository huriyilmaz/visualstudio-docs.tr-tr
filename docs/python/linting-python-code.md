---
title: Python kodu için PyLint kullanma
description: Lint'i özelleştirmek Visual Studio komut satırı seçenekleri de dahil olmak üzere Python kodundaki sorunları kontrol etmek için Visual Studio'de PyLint'i çalıştırın.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7b391a522e9cd1f19e98aa73370d6849977d2142da43a277ae49fa8a7a3235d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367790"
---
# <a name="use-pylint-to-check-python-code"></a>Python kodunu kontrol etmek için PyLint kullanma

Python kodundaki hataları kontrol eden ve iyi Python kodlama desenlerini teşvik eden yaygın olarak kullanılan [pyLint](https://www.pylint.org/)aracı, Python projeleri için Visual Studio tümleşiktir.

## <a name="run-pylint"></a>PyLint'i çalıştırma

Python'daki bir Python projesine sağ **tık Çözüm Gezgini** **Python Run**  >  **PyLint seçeneğini seçmeniz gerekir:**

![Python projeleri için bağlam menüsünde PyLint komutu](media/code-pylint-command.png)

Bu komutu kullanmak, etkin ortamınız yoksa PyLint'i yüklemenizi istenir.

PyLint uyarıları ve hataları Hata **Listesi penceresinde** görüntülenir:

![PyLint hata listesi](media/code-pylint-error-list.png)

Bir hataya çift tıklarsanız doğrudan sorunu oluşturan kaynak koda ulaşabilirsiniz.

> [!Tip]
> Tüm [PyLint çıkış iletilerinin](https://pylint.readthedocs.io/en/latest/technical_reference/features.html) ayrıntılı listesi için bkz. PyLint özellikleri başvurusu.

## <a name="set-pylint-command-line-options"></a>PyLint komut satırı seçeneklerini ayarlama

PyLint [belgelerinin](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) komut satırı seçenekleri *bölümünde,pylintrc* yapılandırma dosyası aracılığıyla PyLint'in davranışını denetleme açıklanmıştır. Bu tür bir dosya, bu ayarların ne kadar geniş bir şekilde uygulanmasını istediğinize bağlı olarak Visual Studio'de veya başka bir yerde Python projesinin köküne yer değiştirebilir (ayrıntılar için komut satırı [seçeneklerine](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) bakın).

Örneğin, bir projede *.pylintrc* dosyasıyla önceki görüntüde gösterilen "eksik docstring" uyarılarını göstermeden önce adımları uygulayın:

1. Komut satırına proje kökünü *(.pyproj* dosyanızı içerir) gidin ve açıklama satırı yapılan bir yapılandırma dosyası oluşturmak için aşağıdaki komutu çalıştırın:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. Bu Visual Studio Çözüm Gezgini projenize sağ tıklayın, Var Olan Öğeyi Ekle'yi seçin, yeni  >   *.pylintrc* dosyasına gidin, seçin ve Ekle'yi **seçin.**

1. Üzerinde çalışabilirsiniz çeşitli ayarları olan dosyayı düzenlemek için açın. Bir uyarıyı devre dışı bırakmak `[MESSAGES CONTROL]` için bölümünü bulun ve ilgili `disable` bölümdeki ayarı bulun. Uzun bir belirli ileti dizesi içerir ve bu dizeye istediğiniz uyarıları eklersiniz. Buradaki örnekte ekleme `,missing-docstring` (satır içi virgül dahil).

1. Uyarıların artık gizlenmelerini görmek için *.pylintrc* dosyasını kaydedin ve PyLint'i yeniden çalıştırın.

> [!Tip]
> Bir ağ *paylaşımından .pylintrc* dosyası kullanmak için, UNC yolu veya eşlenmiş bir sürücü harfi kullanarak ağ paylaşımında dosya adı değeriyle adlı bir `PYLINTRC` ortam değişkeni oluşturun. Örneğin, `PYLINTRC=\\myshare\python\.pylintrc`.
