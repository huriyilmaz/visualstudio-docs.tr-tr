---
title: Subversion Deposu Ayarlama
description: Mac için Visual Studio'da Subversion'ı kullanma.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: 7d95c73b8d745826b256d515f161194ee9dbb587
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692380"
---
# <a name="set-up-a-subversion-repository"></a>Bir Subversion deposu ayarlama

Subversion merkezi bir _sürüm kontrol sistemidir,_ yani tüm dosyaları ve düzeltmeleri içeren tek bir sunucu vardır, bu da kullanıcıların herhangi bir dosyanın herhangi bir sürümünü kontrol edebilirsiniz. Dosyalar uzak bir Subversion deposundan kullanıma alındığında, kullanıcı o anda deponun anlık görüntüsünü alır.

Sürüm denetiminiz için Subversion'u kullanmak için makinenize yüklenmesi gerekir. Subversion makinenizin yüklü olup olmadığını kontrol etmek için Terminal'de aşağıdaki komutu kullanın:

```bash
svn --version
```

Bu komut sürüm numarasını döndürür.

Subversion zaten yüklü değilse, bunu elde etmenin en kolay yolu _Xcode Komut Satırı Araçları_yükleyerek. Xcode Komut Satırı Araçları ve Subversion yüklemek için aşağıdaki komutu kullanın.

```bash
xcode-select --install
```

Subversion makinenize yüklendikten sonra, projenizi SVN'de yayınlamak için aşağıdaki adımları kullanın.

1. Çevrimiçi ücretsiz bir SVN deposu oluşturun. Bu [örnekiçin, Assembla](https://app.assembla.com/) kullanılmıştır. Oluşturulduktan sonra, depoya bağlanmak için kullanılacak bir URL sağlanacaktır:

    ![SVN URL'sini kopyalama](media/version-control-subversion1-sml.png)

2. Mac Project için bir Görsel Stüdyo açın veya oluşturun.

3. Proje'ye sağ tıklayın ve **Sürüm Denetimi'ni seçin > Sürüm Denetimi'nde yayınlayın...**:

    ![Yayına Başla Projesi](media/version-control-subversion2.png)

4. **Depoya Bağlan** sekmesinde, üst açılır yerden **Alt Sürüm'u** seçin.

5. URL'yi adım 1'den girin. URL girildikten sonra, diğer alanlar varsayılan olarak doldurulur:

    ![Depo'nu seçin ve ayrıntıları girin İletişim](media/version-control-subversion3.png)

7. **Tamam'ı** tıklatın ve sonra Yayımla'ya basarak **onaylayın.**

7. İstenirse, depoyu oluşturduğunuz siteiçin kimlik bilgilerinizi aşağıda gösterildiği gibi girin:

    ![Alt sürüm repo için kimlik bilgileri girme](media/version-control-subversion5.png)

8. Kullanılabilir tüm sürüm denetim komutları artık sürüm denetim menüsünde görünür olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Subversion ile çalışma](working-with-subversion.md)