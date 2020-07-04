---
title: Subversion Deposu Ayarlama
description: Mac için Visual Studio alt sürüm kullanılıyor.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.topic: how-to
ms.openlocfilehash: ae67bdd9a9dac8daed268105d830064fa6ef4cae
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950413"
---
# <a name="set-up-a-subversion-repository"></a>Bir alt sürüm deposu ayarlama

Alt sürüm, tüm dosyaları ve düzeltmeleri içeren tek bir sunucu olan ve kullanıcıların herhangi bir dosyanın herhangi bir sürümünü denetleyebileceği bir merkezi _sürüm denetim sistemidir_. Dosyalar uzak bir alt sürüm deposundan kullanıma alındığı zaman, Kullanıcı o anda deponun anlık görüntüsünü alır.

Sürüm denetiminizin alt sürümünü kullanmak için makinenizde yüklü olması gerekir. Makinenizin alt sürümünün yüklenip yüklenmediğini denetlemek için terminalde aşağıdaki komutu kullanın:

```bash
svn --version
```

Bu komut, sürüm numarasını döndürür.

Alt sürüm zaten yüklü değilse, _Xcode komut satırı araçlarının_yüklenmesi en kolay yoldur. Xcode komut satırı araçlarını ve alt sürümünü yüklemek için aşağıdaki komutu kullanın.

```bash
xcode-select --install
```

Makinenizde alt sürüm yüklendikten sonra, SVN 'de projenizi yayımlamak için aşağıdaki adımları kullanın.

1. Çevrimiçi olarak ücretsiz bir SVN deposu oluşturun. Bu örnekte, bir veya daha fazla [birleştirme](https://app.assembla.com/) kullanıldı. Oluşturulduktan sonra, depoya bağlanmak için kullanılacak bir URL sunulacaktır:

    ![SVN URL 'sini Kopyala](media/version-control-subversion1-sml.png)

2. Bir Mac için Visual Studio projesi açın veya oluşturun.

3. Projeye sağ tıklayın ve sürüm **denetiminde yayımla > sürüm denetimi ' ni seçin...**:

    ![Projeyi yayımlamaya başla](media/version-control-subversion2.png)

4. **Depoya Bağlan** sekmesinde üst açılan kutudan **alt sürüm** ' ü seçin.

5. Adım 1 ' den URL 'YI girin. URL girildiğinde, diğer alanlar varsayılan olarak doldurulur:

    ![Depo seçin ve ayrıntıları girin Iletişim kutusu](media/version-control-subversion3.png)

7. **Tamam** ' a tıklayın ve ardından **Yayımla**' ya basarak onaylayın.

7. İstenirse, depoyu oluşturduğunuz sitenin kimlik bilgilerini aşağıda gösterildiği gibi girin:

    ![Alt sürüm deposu için kimlik bilgilerini girme](media/version-control-subversion5.png)

8. Kullanılabilir tüm sürüm denetimi komutları artık sürüm denetim menüsünde görünür olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Subversion ile çalışma](working-with-subversion.md)