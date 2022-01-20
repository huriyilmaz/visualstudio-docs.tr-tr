---
title: 'izlenecek yol: Visual Studio uzantısını yayımlama | Microsoft Docs'
description: Visual Studio uzantısını Visual Studio market 'e yayımlamayı öğrenin. bu, geliştiricilerin yeni ve güncelleştirilmiş uzantılara gözatmasına olanak tanır.
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
ms.openlocfilehash: 2f985201a31381b233a8e4c91af9fb62eb169f97
ms.sourcegitcommit: 1c0eda2db1b1fff9595ca644503f467bf3e223e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "137095065"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>izlenecek yol: Visual Studio uzantısını yayımlama

bu izlenecek yol, Visual Studio market 'e Visual Studio uzantısının nasıl yayımlanacağını göstermektedir. uzantınızı Visual Studio market 'e eklediğinizde, geliştiriciler yeni ve güncelleştirilmiş uzantılara gözatabilmeniz için **uzantıları ve güncelleştirmeleri** kullanabilir.

## <a name="prerequisites"></a>Önkoşullar

 bu yönergeyi izlemek için Visual Studio SDK 'sını yüklemelisiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Visual Studio uzantısı oluşturma

Bu makale varsayılan VSPackage uzantısını kullanır, ancak adımlar her tür uzantı için geçerlidir.

- Bir menü komutu olan adlı C# adlı bir VSPackage oluşturun `TestPublish` . Daha fazla bilgi için bkz. [ilk uzantınızı oluşturma: Merhaba Dünya](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Uzantınızı paketleyin

1. *. Valtmanifest* uzantısını ürün adı, yazarı ve sürümü hakkında doğru bilgilerle güncelleştirin.

   ![Uzantı valtbildirimini Güncelleştir](media/update-extension-vsixmanifest.png)

2. Uzantınızı **yayın** modunda derleyin. Artık uzantınız, \bin\Release klasöründe bir VSıX olarak paketlenmiştir.

3. Yüklemeyi doğrulamak için VSıX 'e çift tıklayabilirsiniz.

## <a name="test-the-extension"></a>Uzantıyı test etme

 Uzantıyı dağıtmadan önce, Visual Studio deneysel örneğine doğru yüklendiğinden emin olmak için oluşturun ve test edin.

1. Visual Studio, Visual Studio deneysel bir örneğini açmak için hata ayıklamayı başlatın.

2. Deneysel örnekte, **Araçlar** menüsüne gidin ve **Uzantılar ve güncelleştirmeler**' e tıklayın. TestPublish uzantısı Orta bölmede görünmelidir ve etkinleştirilmelidir.

3. **Araçlar** menüsünde, test komutunu görtığınızdan emin olun.

## <a name="publish-the-extension-to-visual-studio-marketplace"></a>uzantıyı Visual Studio market 'e yayımlayın

1. Uzantınızın yayın sürümünü derlediğinizden ve güncel olduğundan emin olun.

2. bir web tarayıcısında [Visual Studio marketi](https://marketplace.visualstudio.com/vs)' ne gidin.

3. Sağ üst köşede **oturum aç**' a tıklayın.

4. Oturum açmak için Microsoft hesabı kullanın. Bir Microsoft hesabı yoksa, bu noktada bir tane oluşturabilirsiniz.

5. **Uzantıları Yayımla**' ya tıklayın. Bu seçenek sizi tüm uzantılarınızın Yönet sayfasına yönlendirir. Yayımcı hesabınız yoksa şu anda bir tane oluşturmanız istenir.

   ![market 'e Upload](media/upload-to-marketplace.png)

6. Uzantınızı karşıya yüklemek için kullanmak istediğiniz yayımcıyı seçin. Sol tarafta listelenen yayımcı adlarına tıklayarak yayımcıları değiştirebilirsiniz. **Yeni uzantı** ' a tıklayıp **Visual Studio** seçin.

7. **1: Upload uzantısında**, bir vsıx dosyasını doğrudan Visual Studio market 'e yüklemeyi veya yalnızca kendi web sitenizin bağlantısını eklemeyi seçebilirsiniz. Bu örnekte, *TestPublish. vsix* uzantısı karşıya yüklenir. Uzantınızı sürükleyip bırakın veya dosyaya gitmek için **tıklama** bağlantısını kullanın. Uzantınızı projenin \bin\Release klasöründe bulun.  **Devam**’a tıklayın.

8. **2: uzantı ayrıntılarını sağlayın**, bazı alanlar uzantıınızdan *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur. Aşağıdakiler hakkında daha fazla ayrıntı bulun:

    * **Iç ad** , uzantının ayrıntı sayfasının URL 'sinde kullanılır. Örneğin, "MyName" yayımcı adı altında bir uzantı yayımlamak ve dahili adı "uzantım" olacak şekilde belirtmek, \. uzantınızın ayrıntı sayfası için "Market. VisualStudio com/Items? ItemName = myname. MyExtension" URL 'si ile sonuçlanır.

    * Uzantınızın **görünen adı** . Bu ad, *Source. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    * Karşıya yüklediğiniz uzantının **Sürüm** numarası. Bu sürüm, *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    * **vsıx kimliği** , Visual Studio uzantınızın kullandığı benzersiz tanıtıcıdır. Uzantınızın otomatik güncelleştirilmesini istiyorsanız bu tanımlayıcı gereklidir. Bu tanımlayıcı, *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    * Uzantınız için kullanılan **logo** . Bu logo, sağlanmışsa *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    * Uzantınızın ne yaptığını **kısa bir açıklama** . Bu açıklama, *Source. Extension. valtmanifest* dosyasından otomatik olarak doldurulur.

    * **Genel bakış** , dahili ekran görüntülerini ve uzantınızın ne yaptığını hakkında ayrıntılı bilgileri içerecek şekilde iyi bir yerdir.

    * **desteklenen Visual Studio sürümleri** , uzantınızın hangi Visual Studio sürümüne çalışabileceği arasından seçim yapmanızı sağlar. Uzantınızın yalnızca bu sürümlere yüklenmiş olması.

    * **desteklenen Visual Studio sürümü** , uzantınızın Visual Studio hangi sürümlerinin çalışabileceği seçmenize olanak sağlar. Uzantınız yalnızca bu sürümlere yüklenir.

    * **Yazın**. En yaygın uzantı türü **araçlardır**.

    * **Kategoriler**. Uzantınıza en uygun olan en fazla üç seçin.

    * **Etiketler** , kullanıcıların uzantınızı bulmasına yardımcı olan anahtar sözcüklerdir. etiketler, Visual Studio market 'teki uzantılarınızın arama uygunluğunu artırmaya yardımcı olabilir.

    * **Fiyatlandırma kategorisi** , uzantınızın maliyetidir.

    * **Kaynak kodu deposu** , topluluk ile kaynak kodunuzun bağlantısını paylaşmanıza olanak sağlar.

    * **Uzantınız Için Q&A 'Nın Izin verme** özelliği, kullanıcıların uzantı giriş sayfanızda soru bırakabilir.

9. **& kaydet**' e tıklayın upload. Bu seçenek sizi yayımcı yönetimi sayfanıza geri götürür. Uzantınız henüz yayımlanmadı.

10. Uzantınızı yayımlamak için uzantınızın üzerine sağ tıklayıp **ortak yap**' ı seçin. uzantınızın Visual Studio marketi 'nde nasıl görüneceğine bakmak için **uzantıyı görüntüle**' yi seçin. Alım numaraları için **raporlar**' a tıklayın. Uzantınızın üzerinde değişiklik yapmak için **Düzenle**'ye tıklayın.

    ![Uzantı giriş menüsü](media/extension-entry-menu.png)

11. **Genel yap**' a tıklayın ve uzantınızın artık genel olması gerekir. uzantınızın Visual Studio market 'i arayın.

## <a name="update-a-published-extension-in-visual-studio-marketplace"></a>Visual Studio marketi 'nde yayımlanmış bir uzantıyı güncelleştirme

Başlamadan önce, uzantınızın yeni yayın sürümünü oluşturduğunuzdan ve güncel olduğundan emin olun.

1.  bir web tarayıcısında [Visual Studio marketi](https://marketplace.visualstudio.com/vs)' ne gidin.

1.  Sağ üst köşede **oturum aç**' a tıklayın ve ardından Microsoft hesabı oturum açın.

    :::image type="content" source="media/marketplace-upload-extension.png" alt-text="Dosya Gezgini 'nde karşıya yüklenen bir uzantı dosyasını seçmeyi gösteren ekran görüntüsü.":::

1.  **Uzantıları Yayımla**' ya tıklayın ve ardından, güncelleştirilmiş uzantınızı karşıya yüklemek için kullanmak istediğiniz yayımcıyı seçin.

    :::image type="content" source="media/marketplace-select-extension-version.png" alt-text="uzantıları yayımla bağlantısı vurgulanmış Visual Studio marketi 'nin ekran görüntüsü.":::

1.  Güncelleştirmek istediğiniz uzantının yanında, farenizi üç yatay nokta üzerine getirin ve ardından **Düzenle**' yi seçin.

    :::image type="content" source="media/marketplace-select-extension.png" alt-text="Düzenlenecek uzantıyı seçmeyi gösteren ekran görüntüsü.":::

1.  **1: Upload uzantısı**, vsıx dosyanızın adından sonra, yayımlanan uzantınızı düzenlemek için kalem simgesine tıklayın.

     :::image type="content" source="media/marketplace-edit-extension-details.png" alt-text="Uzantınızı düzenlemek için kalem simgesine tıklayan ekran görüntüsü.":::

1.  Güncelleştirilmiş uzantı VSıX dosyanıza gidin. Dosyaya ve sonra **Aç**' a tıklayın.

    Güncelleştirilmiş uzantınız karşıya yüklenir.

    :::image type="content" source="media/marketplace-upload-extension-notification.png" alt-text="Düzenlenmiş bir uzantıyı karşıya yükledikten sonra karşıya dosya yükleme bildiriminin ekran görüntüsü.":::

1. **2: uzantı ayrıntılarını belirtin**, bazı ayrıntılar uzantı güncelleştirmesi için salt okunurdur veya uzantıınızdan *kaynak. Extension. valtmanifest* dosyasından otomatik olarak doldurulur. Uzantı ayrıntıları hakkında daha fazla bilgi aşağıdadır:

    - **Iç ad** \* , uzantının ayrıntı sayfasının URL 'sinde kullanılır. Örnek olarak, "MyName" yayımcı adı altında bir uzantı yayımlamak ve dahili adı "My extenm" olarak belirtmek, uzantınızın ayrıntı sayfası için "marketplace.visualstudio.com/items?itemName=myname.myextension" URL 'SI ile sonuçlanır.

    - **Görünen Ad** \* uzantısını kullanır. Bu ad *source.extension.vsixmanifest dosyasından otomatik olarak* doldurulur.

    - **Sürüm** \* karşıya yüklediğiniz uzantının sayısı. Bu sürüm, *source.extension.vsixmanifest dosyasından otomatik olarak* doldurulur.

    - **VSIX Kimliği** \* , uzantınız için Visual Studio benzersiz tanımlayıcıdır. Uzantınızı otomatik olarak güncelleştirilir yapmak için bu tanımlayıcı gereklidir. Bu tanımlayıcı *source.extension.vsixmanifest dosyasından otomatik olarak* doldurulur.

    - **Logo** \* bu, uzantınız için kullanılır. Bu logo, sağlanan *source.extension.vsixmanifest dosyasından* otomatik olarak doldurulur.

    - **Kısa açıklama** \* uzantısının ne yaptığını. Bu açıklama *source.extension.vsixmanifest dosyasından otomatik olarak* doldurulur.

    - **Genel** bakış, uzantının ne yaptığına ilişkin ekran görüntülerini ve ayrıntılı bilgileri eklemek için iyi bir yerdir.

    - **Desteklenen Visual Studio sürümleri,** \* uzantınız için hangi Visual Studio sürümlerini seçmenize olanak sağlar. Uzantınız yalnızca bu sürümlere yüklenir.

    - **Desteklenen Visual Studio sürümü,** \* uzantınız üzerinde çalışacak Visual Studio sürümleri seçmenize olanak sağlar. Uzantınız yalnızca bu sürümlere yüklenir.

    - **yazın.** En yaygın uzantı türü **Araçlar'dır.**

    - **Kategorileri.** Uzantınıza en uygun olan üçe kadar seçim yapabilirsiniz.

    - **Etiketler,** kullanıcıların uzantınızı bulmalarını yardımcı olan anahtar sözcüklerdir. Etiketler, Market'te uzantılarınız için arama ilgi düzeyinin Visual Studio olabilir.

    - **Fiyatlandırma Kategorisi,** uzantının maliyetidir.

    - **Kaynak kod deposu,** kaynak kodunuzun bağlantısını toplulukla paylaşmanıza olanak sağlar.

    - **Uzantınız için&A'ya izin ver,** kullanıcıların uzantı giriş sayfanıza soru bırakmasına olanak sağlar.

       \* Uzantı güncelleştirmesi için bu ayrıntı değiştirilemez.

1. **Kaydet'e & Upload.** Bu seçenek sizi yayımcı yönetimi sayfanıza geri alır. Uzantınız henüz yayımlanmadı.

1. Uzantınızı yayımlamak için uzantınıza sağ tıklayın ve Genel'i **seçin.** Uzantının Market'te nasıl Visual Studio görmek için Uzantıyı **Görüntüle'yi seçin.** Alım numaraları için Raporlar'a **tıklayın.** Uzantınız üzerinde değişiklik yapmak için Düzenle'ye **tıklayın.**

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Yayımcı hesabı yönetmek için başka kullanıcılar ekleme

Visual Studio Market, bir yayımcı hesabına erişmek ve bu hesabı yönetmek için ek kullanıcı izinleri verilmesini destekler.

1. Ek kullanıcı eklemek istediğiniz yayımcı hesabına gidin.

2. **Üyeler'i** seçin ve Ekle'ye **tıklayın.**

   ![Ek Kullanıcı Ekle](media/add-users.png)

3. Daha sonra eklemek istediğiniz kullanıcının e-posta adresini belirtebilirsiniz ve Rol seçin altında doğru erişim **düzeyini belirtebilirsiniz.**  Aşağıdaki seçeneklerden birini belirtebilirsiniz:

   * **Oluşturucu:** Kullanıcı uzantıları yayımlar, ancak diğer kullanıcılar tarafından yayımlanan uzantıları görüntüamaz veya yönetamaz.

   * **Okuyucu:** Kullanıcı uzantıları görüntülemenizi sağlar, ancak uzantıları yayımlar veya yönetamaz.

   * **Katkıda** Bulunan: Kullanıcı uzantıları yayımlar ve yönetebilir, ancak yayımcı ayarlarını düzenleyemez veya erişimi yönetamaz.

   * **Sahip:** Kullanıcı uzantıları yayımlar ve yönetebilir, yayımcı ayarlarını düzenleyebilir ve erişimi yönetebilir.

### <a name="troubleshoot-adding-a-user-to-the-publisher-account"></a>Yayımcı hesabına kullanıcı ekleme sorunlarını giderme

Yayımcı profiline e-posta adresini kullanarak bir kullanıcı eklerken hatasını `TF14045: The identity could not be found` alabilirsiniz.

Bu hatayı önlemek için kullanıcının kullanıcı kimliğini e-posta adresi yerine kullanarak yayımcı hesabına ekleyin. Bir kullanıcının kullanıcı kimliğini bulmak için Visual Studio Market'te bölmenin üst kısmında kullanıcının adının üzerine gelin. Kullanıcı kimliğini kopyalamak için kopyala simgesini seçin.

![Market'te bir kullanıcının adının ve e-posta adresinin yanındaki kullanıcı kimliğini gösteren ekran görüntüsü.](media/marketplace-user-id.png)

Daha [sonra, kullanıcı kimliğini kullanarak](#add-additional-users-to-manage-your-publisher-account) yeni kullanıcı eklemek için.

## <a name="install-the-extension-from-visual-studio-marketplace"></a>Uzantıyı Market'Visual Studio yükleme

Artık uzantı yayımlanır ve uzantıyı Visual Studio orada test etmek için yükleyin.

1. Bu Visual Studio Araçlar menüsünde **Uzantılar** ve **Güncelleştirmeler'e tıklayın.**

2. **Çevrimiçi'ne** tıklayın ve **TestPublish araması için arama.**

3. **İndir**’e tıklayın. Uzantı daha sonra yüklenmek üzere zamanlandı.

4. Yükleme işlemini tamamlamak için tüm örnek örneklerini Visual Studio.

## <a name="remove-the-extension"></a>Uzantıyı kaldırma

Uzantıyı Market'Visual Studio bilgisayarınızdan kaldırabilirsiniz.

### <a name="to-remove-the-extension-from-visual-studio-marketplace"></a>Uzantıyı Market'Visual Studio kaldırmak için

1. [Market'Visual Studio gidin.](https://marketplace.visualstudio.com/vs)

2. Sağ üst köşeden Uzantıları **yayımla'ya** tıklayın. TestPublish'i yayımlamak için **kullanılan yayımcıyı seçin.** **TestPublish listesi** görüntülenir.

3. Uzantı girişe sağ tıklayın ve **Kaldır'a tıklayın.** Uzantıyı kaldırmak istemenizi onaylamanız istener. **Tamam**'a tıklayın.

### <a name="to-remove-the-extension-from-your-computer"></a>Uzantıyı bilgisayarınızdan kaldırmak için

1. Bu Visual Studio Araçlar menüsünde **Uzantılar** ve **Güncelleştirmeler'e tıklayın.**

2. **TestPublish'i seçin** ve **kaldır'a tıklayın.** Uzantı daha sonra kaldırılmak üzere zamanlandı.

3. Kaldırma işlemini tamamlamak için tüm örnek örneklerini Visual Studio.
