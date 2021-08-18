---
title: 'Adım adım kılavuz: Visual Studio uzantısını | Microsoft Docs'
description: Geliştiricilerin yeni ve Visual Studio uzantılara göz atmalarına olanak sağlayan Visual Studio Market'te bir uzantı yayımlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/15/2021
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 53fa4543bd56bd85f58b5c4251af19300a12fecf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109818"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Adım adım kılavuz: Visual Studio yayımlama

Bu kılavuzda Market'te bir Visual Studio uzantısını Visual Studio gösterir. Uzantınızı Market'e Visual Studio, geliştiriciler yeni ve güncelleştirilmiş uzantılara **göz** atmak için Uzantılar ve Güncelleştirmeler'i kullanabilir.

## <a name="prerequisites"></a>Önkoşullar

 Bu izlenecek yolu takip etmek için Visual Studio SDK'sı yüklemeniz gerekir. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-visual-studio-extension"></a>Bir Visual Studio oluşturma

Bu makalede varsayılan VSPackage uzantısı kullanılır, ancak adımlar her tür uzantı için geçerlidir.

- C# içinde menü komutu olan adlı bir VSPackage `TestPublish` oluşturun. Daha fazla bilgi için [bkz. İlk uzantınızı oluşturma: Merhaba Dünya.](../extensibility/extensibility-hello-world.md)

## <a name="package-your-extension"></a>Uzantınızı paketle

1. *.vsixmanifest uzantısını ürün* adı, yazarı ve sürümü hakkında doğru bilgilerle güncelleştirin.

   ![uzantı vsixmanifest'i güncelleştirme](media/update-extension-vsixmanifest.png)

2. Uzantınızı Yayın **modunda** derleme. Artık uzantınız \bin\Release klasöründe VSIX olarak paketlenmiştir.

3. VsIX'e çift tıklar ve yükleme işlemini doğrularsınız.

## <a name="test-the-extension"></a>Uzantıyı test etmek

 Uzantıyı dağıtmadan önce, uzantıyı derlemek ve test etmek için uzantının deneysel Visual Studio.

1. Bu Visual Studio deneysel bir örnek açmak için hata ayıklamaya Visual Studio.

2. Deneysel örnekte Araçlar menüsüne gidin **ve Uzantılar** ve **Güncelleştirmeler'e tıklayın.** TestPublish uzantısı orta bölmede görün olmalı ve etkinleştirilmelidir.

3. Araçlar **menüsünde** test komutunu gördüğünüzden emin olun.

## <a name="publish-the-extension-to-visual-studio-marketplace"></a>Uzantıyı Market'te Visual Studio yayımlama

1. Uzantının Yayın sürümünü ve güncel olduğundan emin olun.

2. Bir web tarayıcısında [Market'Visual Studio gidin.](https://marketplace.visualstudio.com/vs)

3. Sağ üst köşede oturum **açma'ya tıklayın.**

4. Oturum Microsoft hesabı için oturum açma bilgilerinizi kullanın. Henüz bir Microsoft hesabı, bu noktada bir tane oluşturabilirsiniz.

5. Uzantıları **yayımla'ya tıklayın.** Bu seçenek, tüm uzantılarınız için yönet sayfasına gidin. Yayımcı hesabınız yoksa şu anda bir tane oluşturmanız istenir.

   ![Upload Market'e](media/upload-to-marketplace.png)

6. Uzantınızı karşıya yüklemek için kullanmak istediğiniz yayımcıyı seçin. Sol tarafta listelenen yayımcı adlara tıklayarak yayımcıları değiştirebilirsiniz. Yeni **uzantı'ya** tıklayın **ve** Visual Studio.

7. **1: Upload** uzantısını kullanarak vsIX dosyasını doğrudan Visual Studio Market'e yükleyebilir veya kendi web sitenize bir bağlantı layabilirsiniz. Bu örnekte *TestPublish.vsix uzantısı* karşıya yüklendi. Uzantınızı sürükleyip bırakın veya dosyaya **göz atmak** için tıklama bağlantısını kullanın. Uzantınızı projenin \bin\Release klasöründe bulun.  **Devam**’a tıklayın.

8. **2: Uzantı ayrıntılarını girin;** bazı alanlar uzantınız *tarafından source.extension.vsixmanifest* dosyasından otomatik olarak doldurulur. Aşağıda her biri hakkında daha fazla ayrıntı bulabilirsiniz:

    * **Dahili Ad,** uzantının ayrıntı sayfasının URL'sinde kullanılır. Örneğin, "myname" yayımcı adı altında bir uzantı yayımlamak ve dahili adı "uzantım" olarak belirtmek, uzantının ayrıntı sayfası için "marketplace.visualstudio \. com/items?itemName=myname.myextension" URL'sine neden olur.

    * **Uzantının** Görünen Adı. Bu ad *source.extension.vsixmanifest dosyasından otomatik olarak* doldurulur.

    * **Karşıya** yüklediğiniz uzantının sürüm numarası. Bu sürüm, *source.extension.vsixmanifest dosyasından otomatik olarak* doldurulur.

    * **VSIX Kimliği,** uzantınız için Visual Studio benzersiz tanımlayıcıdır. Uzantınızı otomatik olarak güncelleştirilir yapmak için bu tanımlayıcı gereklidir. Bu tanımlayıcı *source.extension.vsixmanifest dosyasından otomatik olarak* doldurulur.

    * **Uzantınız** için kullanılan logo. Bu logo, sağlanan *source.extension.vsixmanifest dosyasından* otomatik olarak doldurulur.

    * **Uzantının** ne yaptığına ilişkin kısa açıklama. Bu açıklama *source.extension.vsixmanifest dosyasından otomatik olarak* doldurulur.

    * **Genel** bakış, uzantının ne yaptığına ilişkin ekran görüntülerini ve ayrıntılı bilgileri eklemek için iyi bir yerdir.

    * **Desteklenen Visual Studio sürümleri,** uzantınız için hangi Visual Studio sürümlerini seçmenize olanak sağlar. Uzantınız yalnızca bu sürümlere yüklenir.

    * **Desteklenen Visual Studio sürümü,** uzantınız için hangi Visual Studio çalışacaklarını seçmenize olanak sağlar. Uzantınız yalnızca bu sürümlere yüklenir.

    * **yazın.** En yaygın uzantı türü **Araçlar'dır.**

    * **Kategorileri.** Uzantınıza en uygun olan üçe kadar seçim yapabilirsiniz.

    * **Etiketler,** kullanıcıların uzantınızı bulmalarını yardımcı olan anahtar sözcüklerdir. Etiketler, Market'te uzantılarınız için arama ilgi düzeyinin Visual Studio olabilir.

    * **Fiyatlandırma Kategorisi,** uzantının maliyetidir.

    * **Kaynak kod deposu,** kaynak kodunuzun bağlantısını toplulukla paylaşmanıza olanak sağlar.

    * **Uzantınız için&A'ya izin ver,** kullanıcıların uzantı giriş sayfanıza soru bırakmasına olanak sağlar.

9. **Kaydet'e & Upload.** Bu seçenek sizi yayımcı yönetimi sayfanıza geri alır. Uzantınız henüz yayımlanmadı.

10. Uzantınızı yayımlamak için uzantınıza sağ tıklayın ve Genel **Hale'yi seçin.** Uzantının Market'te nasıl görüntü Visual Studio için Uzantıyı **Görüntüle'yi seçin.** Alım numaraları için Raporlar'a **tıklayın.** Uzantınız üzerinde değişiklik yapmak için Düzenle'ye **tıklayın.**

    ![Uzantı Girişi Menüsü](media/extension-entry-menu.png)

11. Genel **Hale Ekle'ye** tıklayın; uzantınız artık geneldir. Uzantınız Visual Studio Market'te arama yapabilirsiniz.

## <a name="update-a-published-extension-in-visual-studio-marketplace"></a>Visual Studio Market'te yayımlanmış bir uzantıyı güncelleştirme

Başlamadan önce, uzantının yeni yayın sürümünü ve güncel olduğundan emin olun.

1.  Bir web tarayıcısında [Market'Visual Studio gidin.](https://marketplace.visualstudio.com/vs)

1.  Sağ üst köşede Oturum açma'ya **tıklayın** ve ardından oturum açma Microsoft hesabı.

    :::image type="content" source="media/marketplace-upload-extension.png" alt-text="Dosya Gezgini'de karşıya yüklenen uzantı dosyasını seçmeyi gösteren ekran Dosya Gezgini.":::

1.  Uzantıları **yayımla'ya** tıklayın ve ardından güncelleştirilmiş uzantınızı karşıya yüklemek için kullanmak istediğiniz yayımcıyı seçin.

    :::image type="content" source="media/marketplace-select-extension-version.png" alt-text="Uzantıları yayımla bağlantısının Visual Studio Market'in ekran görüntüsü.":::

1.  Güncelleştirmek istediğiniz uzantının yanındaki farenizi üç yatay noktanın üzerine gelin ve Düzenle'yi **seçin.**

    :::image type="content" source="media/marketplace-select-extension.png" alt-text="Düzenlemek istediğiniz uzantıyı seçmeyi gösteren ekran görüntüsü.":::

1.  **1: Upload,** VSIX dosya adınızdan sonra yayımlanan uzantınızı düzenlemek için kalem simgesine tıklayın.

     :::image type="content" source="media/marketplace-edit-extension-details.png" alt-text="Uzantınızı düzenlemek için kalem simgesine tıklamayı gösteren ekran görüntüsü.":::

1.  Güncelleştirilmiş uzantı VSIX dosyanıza göz atma. Dosyasına ve ardından Aç'a **tıklayın.**

    Güncelleştirilmiş uzantınız karşıya yükleniyor.

    :::image type="content" source="media/marketplace-upload-extension-notification.png" alt-text="Düzenlenen uzantı karşıya yüklendikten sonra karşıya dosya yükleme bildiriminin ekran görüntüsü.":::

1. **2: Uzantı** ayrıntılarını sağlama, bazı ayrıntılar bir uzantı güncelleştirmesi için salt okunur veya *uzantınız tarafından source.extension.vsixmanifest* dosyasından otomatik olarak doldurulur. Uzantı ayrıntıları hakkında daha fazla bilgi aşağıda veserdedir:

    - **İç Ad** \* uzantının ayrıntı sayfasının URL'sinde kullanılır. Örneğin, "myname" yayımcı adı altında bir uzantı yayımlamak ve dahili adı "uzantım" olarak belirtmek, uzantının ayrıntı sayfası için "marketplace.visualstudio.com/items?itemName=myname.myextension" URL'sini verir.

    - **Görünen ad** \* . Bu ad, *Source. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    - **Sürümü** \* karşıya yüklediğiniz uzantının numarası. Bu sürüm, *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    - **VSıX kimliği** \* Visual Studio uzantınızın kullandığı benzersiz tanıtıcıdır. Uzantınızın otomatik güncelleştirilmesini istiyorsanız bu tanımlayıcı gereklidir. Bu tanımlayıcı, *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    - **Logo** \* Bu, uzantınız için kullanılır. Bu logo, sağlanmışsa *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    - **Kısa açıklama** \* uzantınızın ne yaptığını. Bu açıklama, *Source. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    - **Genel bakış** , dahili ekran görüntülerini ve uzantınızın ne yaptığını hakkında ayrıntılı bilgileri içerecek şekilde iyi bir yerdir.

    - **desteklenen Visual Studio sürümleri** \* uzantınızın hangi Visual Studio sürümünün üzerinde çalışabileceği seçmenize olanak sağlar. Uzantınızın yalnızca bu sürümlere yüklenmiş olması.

    - **desteklenen Visual Studio sürümü** \* uzantınızın hangi Visual Studio sürümlerini seçebilmenizi sağlar. Uzantınızın yalnızca bu sürümlerde yüklü olması.

    - **Yazın**. En yaygın uzantı türü **araçlardır**.

    - **Kategoriler**. Uzantınıza en uygun olan en fazla üç seçin.

    - **Etiketler** , kullanıcıların uzantınızı bulmasına yardımcı olan anahtar sözcüklerdir. etiketler, Visual Studio market 'teki uzantılarınızın arama uygunluğunu artırmaya yardımcı olabilir.

    - **Fiyatlandırma kategorisi** , uzantınızın maliyetidir.

    - **Kaynak kodu deposu** , topluluk ile kaynak kodunuzun bağlantısını paylaşmanıza olanak sağlar.

    - **Uzantınız Için Q&A 'Nın Izin verme** özelliği, kullanıcıların uzantı giriş sayfanızda soru bırakabilir.

       \* Bu ayrıntı, bir uzantı güncelleştirmesi için değiştirilemez.

1. **& kaydet**' e tıklayın upload. Bu seçenek sizi yayımcı yönetimi sayfanıza geri götürür. Uzantınız henüz yayımlanmadı.

1. Uzantınızı yayımlamak için, uzantınızı sağ tıklatın ve **genel yap**' ı seçin. uzantınızın Visual Studio marketi 'nde nasıl görüneceğine bakmak için **uzantıyı görüntüle**' yi seçin. Alım numaraları için **raporlar**' a tıklayın. Uzantınızın üzerinde değişiklik yapmak için **Düzenle**' ye tıklayın.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Yayımcı hesabınızı yönetmek için ek kullanıcılar ekleyin

Visual Studio Market, bir yayımcı hesabına erişmek ve bunları yönetmek için ek kullanıcı izinleri vermeyi destekler.

1. Ek kullanıcı eklemek istediğiniz yayımcı hesabına gidin.

2. **Üyeler** ' i seçin ve **Ekle**' ye tıklayın.

   ![Ek Kullanıcı ekleme](media/add-users.png)

3. Ardından, eklemek istediğiniz kullanıcının e-posta adresini belirtebilir ve **Rol Seç** altında doğru erişim düzeyine sahip olabilirsiniz.  Aşağıdaki seçeneklerden birini belirtebilirsiniz:

   * **Oluşturucu**: Kullanıcı Uzantıları yayımlayabilir, ancak diğer kullanıcılar tarafından yayımlanan uzantıları görüntüleyemez veya yönetemez.

   * **Okuyucu**: Kullanıcı Uzantıları görüntüleyebilir, ancak uzantıları yayımlayamaz veya yönetemez.

   * **Katkıda bulunan**: Kullanıcı Uzantıları yayımlayabilir ve yönetebilir, ancak yayımcı ayarlarını düzenleyemez veya erişimi yönetebilir.

   * **Sahip**: Kullanıcı Uzantıları yayımlayabilir ve yönetebilir, yayımcı ayarlarını düzenleyebilir ve erişimi yönetebilir.

## <a name="install-the-extension-from-visual-studio-marketplace"></a>uzantıyı Visual Studio marketi 'nden yüklemesi

artık uzantı yayımlandığına göre Visual Studio yükleyip test edin.

1. Visual Studio, **araçlar** menüsünde **uzantılar ve güncelleştirmeler**' e tıklayın.

2. **Çevrimiçi** ' e tıklayın ve ardından **TestPublish** için arama yapın.

3. **İndir**’e tıklayın. Uzantı daha sonra yüklenmek üzere zamanlanır.

4. Yüklemeyi gerçekleştirmek için Visual Studio tüm örneklerini kapatın.

## <a name="remove-the-extension"></a>Uzantıyı kaldırma

uzantıyı Visual Studio marketi 'nden ve bilgisayarınızdan kaldırabilirsiniz.

### <a name="to-remove-the-extension-from-visual-studio-marketplace"></a>Visual Studio marketi 'nden uzantıyı kaldırmak için

1. [Visual Studio marketi](https://marketplace.visualstudio.com/vs)' ne gidin.

2. Sağ üst köşede bulunan uzantıları **Yayımla** ' ya tıklayın. **TestPublish** yayımlamak için kullandığınız yayımcıyı seçin. **TestPublish** listesi görüntülenir.

3. Uzantı girişine sağ tıklayın ve **Kaldır**' a tıklayın. Uzantıyı kaldırmak isteyip istemediğinizi onaylamanız istenir. **Tamam**'a tıklayın.

### <a name="to-remove-the-extension-from-your-computer"></a>Uzantıyı bilgisayarınızdan kaldırmak için

1. Visual Studio, **araçlar** menüsünde **uzantılar ve güncelleştirmeler**' e tıklayın.

2. **TestPublish** ' ı seçin ve ardından **Kaldır**' a tıklayın. Uzantı daha sonra kaldırma için zamanlanır.

3. Kaldırma işlemini gerçekleştirmek için Visual Studio tüm örneklerini kapatın.
