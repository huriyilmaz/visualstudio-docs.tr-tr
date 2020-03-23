---
title: Python kodu için PyLint'i kullanma
description: Linting'i özelleştirmek için komut satırı seçenekleri de dahil olmak üzere Python kodundaki sorunları denetlemek için Visual Studio'da PyLint'i çalıştırın.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bf503cff7d8de2c00a93385113de05de00059390
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62956828"
---
# <a name="use-pylint-to-check-python-code"></a>Python kodunu denetlemek için PyLint'i kullanma

Python kodundaki hataları kontrol eden ve iyi Python kodlama desenlerini teşvik eden yaygın olarak kullanılan bir araç olan [PyLint,](https://www.pylint.org/)Python projeleri için Visual Studio'ya entegre edilmiştir.

## <a name="run-pylint"></a>PyLint çalıştırın

**Solution Explorer'da** python projesini sağ tıklatın ve **Python** > **Run PyLint'i**seçin:

![Python projeleri için bağlam menüsünde PyLint komutu](media/code-pylint-command.png)

Bu komutu kullanmak, pyLint'i zaten mevcut değilse etkin ortamınıza yüklemenizi ister.

Hata **Listesi** penceresinde PYLint uyarıları ve hataları görünür:

![PyLint hata listesi](media/code-pylint-error-list.png)

Bir hatayı çift tıklatmak sizi doğrudan sorunu oluşturan kaynak koduna götürür.

> [!Tip]
> Tüm PyLint çıktı iletilerinin ayrıntılı bir listesi için [PyLint özellikleri başvurusuna](https://pylint.readthedocs.io/en/latest/technical_reference/features.html) bakın.

## <a name="set-pylint-command-line-options"></a>PyLint komut satırı seçeneklerini ayarlama

PyLint belgelerinin [komut satırı seçenekleri](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) bölümü, *.pylintrc* yapılandırma dosyası aracılığıyla PyLint'in davranışını nasıl denetleriz açıklar. Böyle bir dosya Visual Studio'da veya başka bir yerde bu ayarların ne kadar yaygın olarak uygulanmasını istediğinize bağlı olarak bir Python projesinin köküne yerleştirilebilir (ayrıntılar için [komut satırı seçeneklerine](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) bakın).

Örneğin, bir projede *bir .pylintrc* dosyası yla önceki resimde gösterilen "eksik docstring" uyarılarını bastırmak için aşağıdaki adımları yapın:

1. Komut satırında, proje kökünüze gidin *(.pyproj* dosyanız var) ve yorumlanan bir yapılandırma dosyası oluşturmak için aşağıdaki komutu çalıştırın:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. Visual Studio Solution Explorer'da projenize sağ tıklayın,**Varolan Öğe** **ekle'yi** > seçin, yeni *.pylintrc* dosyasına gidin, seçin ve **Ekle'yi**seçin.

1. Çalışabileceğiniz birkaç ayar olan düzenleme için dosyayı açın. Bir uyarıyı devre dışı `[MESSAGES CONTROL]` kalmak için `disable` bölümü bulun ve ardından bu bölümdeki ayarı bulun. İstediğiniz uyarıları ekebileceğiniz uzun bir özel ileti dizisi vardır. Buradaki örnekte, ek `,missing-docstring` (delineating virgül dahil).

1. *.pylintrc* dosyasını kaydedin ve uyarıların artık bastırılmış olduğunu görmek için PyLint'i yeniden çalıştırın.

> [!Tip]
> Ağ paylaşımından *.pylintrc* dosyası kullanmak için, UNC yolu veya eşlenen sürücü mektubu kullanarak ağ paylaşımındaki dosya adının değeriyle birlikte adlı `PYLINTRC` bir ortam değişkeni oluşturun. Örneğin, `PYLINTRC=\\myshare\python\.pylintrc`.
