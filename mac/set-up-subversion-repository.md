---
title: Subversion Deposu Ayarlama
description: Subversion'ın bir merkezi sürüm denetimi sistemi olarak nasıl yük yüklerini ve ayarlarını Mac için Visual Studio.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.topic: how-to
ms.openlocfilehash: 573c21a19161781e621c433bbfe26ce2234d080a987a892b7eebe6dc2cb77148
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121438769"
---
# <a name="set-up-a-subversion-repository"></a>Subversion deposu ayarlama

Subversion, merkezi _bir_ sürüm denetim sistemidir. Başka bir ifadeyle, tüm dosyaları ve düzeltmeleri içeren tek bir sunucu vardır ve kullanıcılar herhangi bir dosyanın herhangi bir sürümünü gözden geçirmelerini sağlar. Dosyalar uzak bir Subversion deposundan kullanıma alınarak kullanıma alınarak, kullanıcı deponun o noktada anlık görüntüsünü alır.

Sürüm denetiminiz için Subversion kullanmak üzere makinenize yüklenmiş olması gerekir. Subversion'ın makinenizin yüklü olup olduğunu kontrol etmek için Terminal'de aşağıdaki komutu kullanın:

```bash
svn --version
```

Bu komut sürüm numarasını döndürür.

Subversion yüklü değilse, bunu almanın en kolay yolu Xcode Komut Satırı Araçlarını _yüklemektir._ Xcode Komut Satırı Araçları ve Subversion'ı yüklemek için aşağıdaki komutu kullanın.

```bash
xcode-select --install
```

Subversion makinenize yüklendikten sonra, projenizi SVN'de yayımlamak için aşağıdaki adımları kullanın.

1. Çevrimiçi olarak ücretsiz bir SVN deposu oluşturun. Bu [örnekte, Assembla](https://app.assembla.com/) kullanılmıştır. Oluşturulduktan sonra, depoya bağlanmak için kullanılacak bir URL sağlanır:

    ![SVN URL'sini kopyalama](media/version-control-subversion1-sml.png)

2. Bir dosya açın veya Mac için Visual Studio Project.

3. Sürüm Denetimi'ne sağ Project ve Sürüm **Denetimi'> Yayımla... öğesini seçin:**

    ![Yayımlamaya başlama Project](media/version-control-subversion2.png)

4. Depoya **Bağlan üst açılan** listeden **Subversion'ı** seçin.

5. 1. adımdan URL'yi girin. URL girilirken diğer alanlar varsayılan olarak doldurulur:

    ![Depo'ya Tıklayın ve Ayrıntıları Girin İletişim Kutusu](media/version-control-subversion3.png)

7. **Tamam'a** tıklayın ve yayımla'ya basarak **onaylayın.**

7. İstendiğinde, aşağıda gösterildiği gibi depoyu oluşturmak için sitenin kimlik bilgilerinizi girin:

    ![Subversion depo için kimlik bilgileri girme](media/version-control-subversion5.png)

8. Kullanılabilir tüm sürüm denetimi komutları artık sürüm denetimi menüsünde görünür olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Subversion ile çalışma](working-with-subversion.md)