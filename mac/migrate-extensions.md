---
title: 'Sorun giderme: var olan Uzantımın yeni bir sürümünü Nasıl yaparım? yayınlama?'
description: Yayımlama iş akışı aracılığıyla mevcut uzantıları güncelleştirme Kılavuzu.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/14/2020
ms.technology: vs-ide-general
ms.assetid: 5DA76197-7859-421f-AC45-401F22F5D794
ms.topic: troubleshooting
ms.openlocfilehash: 862ae404571da44d9ca28db2c94d2ebeb39ce79f
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488467"
---
# <a name="troubleshooting-how-do-i-release-a-new-version-of-my-existing-extension"></a>Sorun giderme: var olan Uzantımın yeni bir sürümünü Nasıl yaparım? yayınlama?

> [!IMPORTANT]
> Şu anda, yeni uzantılar oluşturmak Mac için Visual Studio 2019 ' de resmi olarak desteklenmez.

Mac için Visual Studio uzantısı depo sunucusu 15 Ocak 2021 tarihinde taşınır. Bu taşıma, uzantınızı zaten indirmiş olan kullanıcıları etkilemez, ancak bu tarihten sonra uzantınızın yeni sürümlerini yayımlamanıza olanak sağlayacak.

Varolan bir uzantının yazarı olarak, daha fazla güncelleştirme yayınlamak için farklı bir iş akışını izlemeniz gerekir. Bu işlem aşağıdakilerden oluşur:
- Her uzantı için ortak bir GitHub deposu ayarlama
- Depo URL 'sini [uzantı yayımlama posta listesi](mailto:vsmextpub@microsoft.com) ile Mac için Visual Studio ekibine paylaşma
- GitHub 'daki yayınlar özelliğini kullanarak uzantınızı güncelleştirme


## <a name="initial-setup"></a>İlk kurulum 

Uzantılara güncelleştirme yayımlamaya devam edebilmek için genel bir GitHub deposu oluşturmanız gerekir. Birden çok uzantı yayımlarsanız, her zaman birlikte yayımlanmadığınız ve yayımlanmadığınız müddetçe her biri için ayrı bir depoya sahip olmanız gerekir. Bu durumda, tek bir depoyu kullanabilirsiniz.

> [!NOTE]
> Uzantınızın GitHub deposunun ortak olması gerekir, ancak herhangi bir kodunuzda kod barındırmanıza gerek kalmaz. Bu işlemin ardından, GitHub 'da kodunuzun herhangi birine sahip olmanızı gerektirmez.


## <a name="share-the-location-of-your-repository"></a>Deponuzun konumunu paylaşma

Depoyu ayarladıktan sonra [uzantı yayımlama posta lıstesıne](mailto:vsmextpub@microsoft.com) URL ile bir e-posta gönderin.


## <a name="release-a-new-version"></a>Yeni bir sürüm yayınla

Uzantınızı güncelleştirme işlemini başlatmak için deponun ana sayfasında "yeni yayın oluştur" bağlantısını kullanacaksınız. Bu bağlantıyı seçtikten sonra aşağıdaki adımları izleyin:

1. Sürümün **etiket sürümüne** aşağıdaki biçimde bilgi ekleyin

    > v \<releaseVersion> \- VSM\<targetVersion>

    Konum:
     - **&lt; ReleaseVersion &gt;** , uzantınızın sürüm numarasıdır
     - **&lt; TargetVersion &gt;** , uzantınızın hedeflediği Mac için Visual Studio en düşük sürümüdür

2. Seçim **Başlık** ve **Açıklama** alanları istediğiniz bilgilerle doldurulabilir; Bu iş akışı, bu alanlardaki bilgileri kullanmaz.

3. **Yayın öncesi** onay kutusunun işaretinin kaldırıldığından emin olun. Bu onay işaretliyse, yayın bu yayımlama işlemi tarafından çekilmeyecektir.

4. **İkili dosyaları** bölümünde uzantınızı uygulayan **. mpack** dosyalarını ekleyin. Bir yayına birden çok **. mpack** dosyası eklemek mümkündür.

Mac için Visual Studio, uzantınızın uzantı deposuna erişmek için kullanılan Mac için Visual Studio yüklemesiyle uyumlu olan en son sürümünü görüntüler.

GitHub deponuzu Mac için Visual Studio ekiple kaydettiğiniz sürece, dahili sürüm, 24 saat içinde Mac için Visual Studio tarafından alınır.

## <a name="additional-information"></a>Ek bilgiler

- Yukarıda açıklanan gereksinimlere uymayan yayınlar yayımlanmaz. 
- 14 Ocak 2021 ' den sonra, uzantı güncelleştirmeleri yalnızca Mac için Visual Studio 8,0 veya daha yeni bir sürümde görünür.
- Mevcut uzantılar, sizin bölüminizdeki herhangi bir eylemde bulunmadan kullanıcıları Mac için Visual Studio için kullanılabilir olmaya devam edecektir. Yalnızca 15 Ocak 2021 ' den sonra yeni bir sürüm yayımladığınızda bu kılavuzdaki yönergeleri izlemeniz gerekir.
