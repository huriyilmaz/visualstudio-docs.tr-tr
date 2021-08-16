---
title: 'Sorun Giderme: Mevcut uzantımın yeni sürümünü nasıl yayınlarım?'
description: Yayımlama iş akışı aracılığıyla mevcut uzantıları güncelleştirme kılavuzu.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/14/2020
ms.technology: vs-ide-general
ms.assetid: 5DA76197-7859-421f-AC45-401F22F5D794
ms.topic: troubleshooting
ms.openlocfilehash: 921d61da140baa5b4dc36b79de18b0c260b1dd733e0b3089b0a4ff38f300f7ce
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121381590"
---
# <a name="troubleshooting-how-do-i-release-a-new-version-of-my-existing-extension"></a>Sorun Giderme: Mevcut uzantımın yeni sürümünü nasıl yayınlarım?

> [!IMPORTANT]
> Şu anda Mac için 2019'da yeni uzantılar Visual Studio resmi olarak desteklenmiyor.

Uzantı Mac için Visual Studio sunucusu 15 Ocak 2021'de taşınacak. Bu taşıma, uzantınızı indiren kullanıcıları etkilemez, ancak bu tarihten sonra uzantının yeni yayınlarını yayımlama yolunu değiştirir.

Mevcut bir uzantının yazarı olarak, diğer güncelleştirmeleri yayın için farklı bir iş akışını izlemeniz gerekir. Bu işlem şunları oluşur:
- Her uzantı için GitHub depo ayarlama
- Uzantı yayımlama posta listesi aracılığıyla Mac için Visual Studio [ekiple depo URL'sini paylaşma](mailto:vsmextpub@microsoft.com)
- GitHub'daki sürümler özelliğini kullanarak uzantınızı GitHub


## <a name="initial-setup"></a>İlk kurulum 

Uzantılarınıza güncelleştirme yayımlamaya devam etmek için, genel bir GitHub oluşturmanız gerekir. Birden çok uzantı yayımlarsanız, her zaman sürüm ve birlikte yayımlamadıkça her biri için ayrı bir depoya sahip olursunuz; bu durumda tek bir depo kullanabilirsiniz.

> [!NOTE]
> Uzantınız GitHub deponun genel olması gerekir ancak kodunuzun herhangi birini orada barındırmanız gerekli değil. Bu işlemi takip etmek için kodlarınızı herhangi bir GitHub.


## <a name="share-the-location-of-your-repository"></a>Deponun konumunu paylaşma

Depoyu ayar verdiktan sonra UZANTı yayımlama posta listesine URL'si [ile bir e-posta](mailto:vsmextpub@microsoft.com) gönderin.


## <a name="release-a-new-version"></a>Yeni bir sürüm yayınla

Uzantınızı güncelleştirme işlemini başlamak için deponun ana sayfasındaki "Yeni sürüm oluştur" bağlantısını kullanacağız. Bu bağlantıyı seçtikten sonra şu adımları izleyin:

1. Sürümün **etiket sürümüne** aşağıdaki biçimde bilgi ekleyin

    > v \<releaseVersion> \- vsm\<targetVersion>

    Konum:
     - **&lt; releaseVersion, &gt;** uzantı sürüm numaranızdır
     - **&lt; targetVersion, &gt;** uzantınız tarafından Mac için Visual Studio en düşük sürümdür

2. (İsteğe bağlı) Başlık  ve **açıklama** alanları, sizin için herhangi bir bilgiyle doldurulmalıdır; bu iş akışı bu alanlardaki bilgileri kullanmaz.

3. Yayın **öncesi onay kutusunun** işaretlenmemiş olduğundan emin olmak. İşaretlenirse, yayın bu yayımlama işlemi tarafından teslimlanmaz.

4. Uzantınızı **uygulayan .mpack** dosyasını ikili dosyalar **bölümüne** iliştirin. Bir sürümde birden çok **.mpack** dosyası eklemek mümkündür.

Mac için Visual Studio, uzantı depoya erişmek için kullanılan Mac için Visual Studio yüklemesi ile uyumlu en son sürümünü görüntüler.

GitHub deposunu Mac için Visual Studio, uzantı yayınını 24 saat içinde Mac için Visual Studio tarafından alır.

## <a name="additional-information"></a>Ek bilgiler

- Yukarıda belirtilen gereksinimlere uymayan sürümler yayımlanamaz. 
- 15 Ocak 2021'den sonra uzantı güncelleştirmeleri yalnızca Mac için Visual Studio 8.0 veya daha yeni bir sürümde göster.
- Mevcut uzantılar, kullanıcı Mac için Visual Studio herhangi bir işlem yapmadan kullanılabilir durumda kalır. Bu kılavuzda yer alan yönergeleri yalnızca 15 Ocak 2021'den sonra yeni bir sürüm yayımlamanız gerekir.
