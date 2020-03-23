---
title: Tür Üyeleri Oluşturma ve Yapılandırma (Sınıf Tasarımcısı)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfed51812b034d63f250a56548b88f09a98214fe
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590416"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Sınıf Tasarımcısı'nda tür üyeleri oluşturma ve yapılandırma

Bu üyeleri sınıf diyagramındaki türlere ekleyebilir ve **bu** üyeleri Sınıf Ayrıntıları penceresinde yapılandırabilirsiniz:

|**Tür**|**İçerebileceği üyeler**|
|--------------| - |
|Sınıf|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Sabit Listesi|üye|
|Arabirim|yöntem, özellik, olay (C# ve Visual Basic için)|
|Soyut Sınıf|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Yapı (C# için Struct)|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Temsilci|parametre|
|Modül (Yalnızca VB)|yöntem, özellik, alan, olay, oluşturucu, sabit|

> [!NOTE]
> Bir özelliğin get ve set erişimcileri ek mantığa gerek duymadığında, otomatik uygulanan özellikleri (yalnızca C#) kullanarak özellik bildirimini daha kısa yapın. Tam imzayı göstermek için Sınıf **Diyagramı** menüsünden **Üye Biçimlerini** > Tam**İmzayı**Değiştir'i seçin. Otomatik olarak uygulanan özellikler hakkında daha fazla bilgi için [bkz.](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties)

## <a name="common-tasks"></a>Genel görevler

|Görev|İçeriği destekleme|
|----------| - |
|**Başlayın:** Tür üyelerini oluşturmadan ve yapılandırmadan önce **Sınıf Ayrıntıları** penceresini açmanız gerekir.|- [Sınıf Ayrıntıları penceresini açma](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Sınıf Ayrıntıları kullanım notları](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Salt okunur bilgilerin görüntülenmesi](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Sınıf Diyagramı ve Sınıf Ayrıntıları penceresinde klavye ve fare kısayolları](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Tür üyeleri oluşturma ve değiştirme:** **Sınıf Ayrıntıları** penceresini kullanarak yeni üyeler oluşturabilir, üyeleri değiştirebilir ve yönteme parametreler ekleyebilirsiniz.|- [Üye oluşturma](creating-and-configuring-type-members.md#create-members)<br />- [Tür üyelerini değiştirme](creating-and-configuring-type-members.md#modify-type-members)<br />- [Yöntemlere parametreler ekleme](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Sınıf Ayrıntıları penceresini açma

Varsayılan olarak, yeni bir sınıf diyagramı açtığınızda **Sınıf Ayrıntıları** penceresi otomatik olarak görüntülenir. Bkz. [Nasıl: Projelere sınıf diyagramları ekleyin).](how-to-add-class-diagrams-to-projects.md) **Sınıf Ayrıntıları** penceresini aşağıdaki yollarla da açabilirsiniz:

- Bağlam menüsünü görüntülemek için diyagramdaki herhangi bir sınıfa sağ tıklayın ve ardından **Sınıf Ayrıntıları'nı**seçin.

- Menü çubuğundan**Diğer Windows** > **Sınıfı Ayrıntılarını** **Görüntüle'yi** > seçin.

## <a name="create-members"></a>Üye oluşturma

Üye oluşturmak için aşağıdaki araçlardan herhangi birini kullanabilirsiniz:

- **Sınıf Tasarımcısı**

- **Sınıf Ayrıntıları** penceresi araç çubuğu

- **Sınıf Detayları** penceresi

> [!NOTE]
> Bu bölümdeki yordamları kullanarak oluşturucular ve yıkıcılar da oluşturabilirsiniz. Yapıcıların ve yıkıcıların özel yöntem türleri olduğunu ve bu nedenle sınıf diyagramı şekillerinde **Yöntemler** bölmesinde ve **Sınıf Ayrıntıları** pencere ızgarasının **Yöntemler** bölümünde göründüklerini lütfen unutmayın.

> [!NOTE]
> Bir temsilciye ekleyebileceğiniz tek varlık parametredir. 'Sınıf **Ayrıntıları** penceresi araç çubuğunu kullanarak üye oluşturmak için' yordamı bu eylem için geçerli olmadığını unutmayın.

### <a name="create-a-member-using-class-designer"></a>Sınıf Tasarımcısı'nı kullanarak üye oluşturma

1. Üye eklemek istediğiniz türü sağ tıklatın, **Ekle'ye**işaret edin ve eklemek istediğiniz üye türünü seçin.

     Yeni bir üye imzası oluşturulur ve türe eklenir. Sınıf Tasarımcısı'nda, **Sınıf** **Ayrıntıları** penceresinde veya **Özellikler** penceresinde değiştirebileceğiniz varsayılan bir ad verilir.

2. İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Sınıf Ayrıntıları penceresi araç çubuğunu kullanarak üye oluşturma

1. Diyagram yüzeyinde, üye eklemek istediğiniz türü seçin.

     Tür odak alır ve içeriği Sınıf **Ayrıntıları** penceresinde görüntülenir.

2. Sınıf **Ayrıntıları** penceresinde araç çubuğunda, üst teki simgeyi tıklatın ve açılan listeden **Yeni \<üye>** seçin.

     İmleç, eklemek istediğiniz üye türü için üst üste **Ad** alanına taşınır. Örneğin, **Yeni Özellik'i**tıklattıysanız imleç, **Sınıf Ayrıntıları** penceresinin **Özellikler** bölümünde yeni bir satıra taşınır.

3. Oluşturmak istediğiniz üyenin adını yazın ve Enter'a basın (ya da başka bir şekilde, örneğin, Sekme tuşuna basarak odağı taşıyın).

     Yeni bir üye imzası oluşturulur ve türe eklenir. Üye artık kod da bulunur ve **Sınıf Tasarımcısı,** **Sınıf Ayrıntıları** penceresinde ve Özellikler penceresinde görüntülenir.

4. İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="create-a-member-using-the-class-details-window"></a>Sınıf Ayrıntıları penceresini kullanarak üye oluşturma

1. Diyagram yüzeyinde, üye eklemek istediğiniz türü seçin.

     Tür odak alır ve içeriği Sınıf **Ayrıntıları** penceresinde görüntülenir.

2. Sınıf **Ayrıntıları** penceresinde, eklemek istediğiniz üye türünü içeren bölümde üye ** \<>ekle'yi **tıklatın. Örneğin, bir alan eklemek istiyorsanız, ** \<alan>ekle'yi **tıklatın.

3. Oluşturmak istediğiniz üyenin adını yazın ve Enter'a basın.

     Yeni bir üye imzası oluşturulur ve türe eklenir. Üye artık kod da bulunur ve **Sınıf Tasarımcısı,** **Sınıf Ayrıntıları** penceresinde ve Özellikler penceresinde görüntülenir.

4. İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

    > [!NOTE]
    > Üye oluşturmak için klavye kısayollarını da kullanabilirsiniz. Daha fazla bilgi için [Sınıf Diyagramı ve Sınıf Ayrıntıları penceresinde klavye ve fare kısayolları'na](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)bakın.

## <a name="modify-type-members"></a>Tür üyelerini değiştirme

Sınıf Tasarımcısı, diyagram görüntülenen türlerin üyelerinde değişiklik yapmanıza olanak sağlar. Sınıf diyagramında görüntülenen ve salt okunur olmayan her türün üyelerini değiştirebilirsiniz. Tasarım yüzeyinde, Özellikler penceresinde ve **Sınıf Ayrıntıları** penceresinde yerinde düzenleme kullanarak tür üyelerini değiştirirsiniz.

**Sınıf Ayrıntıları** penceresinde görüntülenen tüm üyeler, sınıf diyagramındaki türlerin üyelerini temsil eder. Dört üye türü vardır: yöntemler, özellikler, alanlar ve olaylar.

Tüm üye satırları, üyeleri türe göre gruplandıran başlıkların altında görünür. Örneğin, tüm özellikler, ızgarada düğüm olarak daraltılmış veya genişletilebilen **Özellikler**başlığı altında görünür.

Her üye satırı aşağıdaki öğeleri görüntüler:

- **Üye Simgesi**

     Her üyü türü kendi simgesiyle gösterilir. Üyenin imzasını görüntülemek için fareyi üye simgesine doğru taşırın. Satırı seçmek için, üye simgesine ya da üye simgesinin solundaki boşluğa tıklayın.

- **Üye Adı**

     Üye satırındaki **Ad** sütunu üyenin adını görüntüler. Bu ad, Özellikler penceresindeki **Ad** özelliğinde de görüntülenir. Okuma/Yazma izinlerine sahip herhangi bir üyenin adını değiştirmek için bu hücreyi kullanın.

     **Ad** sütunu tüm adı gösteremeyecek kadar darsa, üye adına fareyi işaret etmek tüm adı görüntüler.

- **Üye Türü**

     **Üye Türü** hücresi, geçerli projede veya başvurulan projelerde bulunan tüm türlerin listesinden seçim yapmanızı sağlayan IntelliSense'i kullanır.

- **Üye Değiştirici**

     Bir üyenin görünürlüğünü değiştiricisini `Public` (`public` `Private` ),`private` `Friend` (`internal` `Protected` (`protected` `Protected Friend` )`protected internal`( `Default`( ), ( ( ), veya .

- **\<üye>ekle**

     **Sınıf Ayrıntıları** penceresindeki son satır, **Ad** hücresinde ki ** \<metin ekle üye>** içerir. Bu hücreye tıklarsanız yeni bir üye oluşturabilirsiniz. Daha fazla bilgi için [bkz.](creating-and-configuring-type-members.md#create-members)

- **Özellikler penceresindeki üye özellikleri**

     **Sınıf Ayrıntıları** penceresi, Özellikler penceresinde görüntülenen üye özelliklerin bir alt kümesini görüntüler. Özelliğin bir konumda değiştirilmesi, özelliğin değerini global olarak güncelleştirir. Değerinin diğer konumda görüntülenmesi de buna dahildir.

- **Özet**

     **Özet** hücresi üye hakkında bir bilgi özetini ortaya çıkarır. **Özet**, **İade Türü**ve Üyenin **Açıklamaları** hakkındaki bilgileri görüntülemek veya döndürmek için **Özet** hücresindeki elipsleri tıklatın.

- **Gizle**

     **Gizle** onay kutusu seçildiğinde, üye türde görüntülenmez.

### <a name="to-modify-a-type-member"></a>Bir tür üyesini değiştirmek için

1. Sınıf Tasarımcısı'nı kullanarak bir tür seçin.

2. Sınıf **Ayrıntıları** penceresi görüntülenmiyorsa, Sınıf Tasarımcısı araç çubuğundaki **Sınıf Ayrıntıları** pencere düğmesini tıklatın.

3. **Sınıf Ayrıntıları** pencere ızgarası alanlarındaki değerleri edin. Her düzenlemeden sonra ENTER'a basın ya da bir başka yolla, örneğin SEKME tuşuna basarak, odağı düzenlenen alanın dışına taşıyın. Düzenlemeleriniz anında koda yansır.

    > [!NOTE]
    > Bir üyenin yalnızca adını değiştirmek istiyorsanız, bunu yerinde düzenlemeyi kullanarak yapabilirsiniz.

## <a name="add-parameters-to-methods"></a>Yöntemlere parametreler ekleme

**Sınıf Ayrıntıları** penceresini kullanarak yöntemlere parametreler ekleyin. Parametreler, zorunlu veya isteğe bağlı olacak şekilde yapılandırılabilir. Bir parametrenin **İsteğe Bağlı Varsayılan** özelliği için bir değer sağlamak, tasarımcıya isteğe bağlı parametre olarak kod oluşturması talimatını verir.

Parametre satırı aşağıdaki öğeleri içerir:

- **Adı**

     Parametre satırındaki **Ad** sütunu parametrenin adını görüntüler. Bu ad, Özellikler penceresindeki **Ad** özelliğinde de görüntülenir. Okuma/Yazma izinlerine sahip herhangi bir parametrenin adını değiştirmek için bu hücreyi kullanabilirsiniz.

     Ad **sütunu** tüm adı göstermek için çok darsa, parametre adına işaret etmek parametrenin adını görüntüler.

- **Tür**

     **Parametre Türü** hücresi, geçerli projede veya başvurulan projelerde bulunan tüm türlerin listesi arasından seçim yapmanızı sağlayan IntelliSense'i kullanır.

- **Değiştirici**

     Parametre satırındaki **Değiştirici** hücresi, parametrenin yeni değiştiricisini kabul eder ve görüntüler. Yeni bir parametre değiştirici girmek için, **Yok,** **ref,** **out,** veya C#'daki **paramlardan** ve **ByVal,** **ByRef**veya VB'deki **ParamArray'den** seçim yapmak için açılır liste kutusunu kullanın.

- **Özet**

     Parametre satırındaki **Özet** hücresi, parametreyi kod düzenleyicisine girerken IntelliSense'de görünen kod yorumlarının girilmesine olanak tanır.

- **\<parametre>ekleyin**

     Bir üyenin son parametre satırı, **Ad** hücresinde **parametre\> eklemek<** metni içerir. Bu hücreye tıklanması yeni bir parametre oluşturmanıza izin verir. Daha fazla bilgi için [bkz.](creating-and-configuring-type-members.md#add-parameters-to-methods)

**Özellikler** **penceresi, Sınıf Ayrıntıları** penceresinde görüntülenen parametre özelliklerini görüntüler: **Ad**, **Tür**, **Değiştirici**, **Özet**, ayrıca **İsteğe Bağlı Varsayılan** özellik. Özelliğin bir konumda değiştirilmesi, özelliğin değerini global olarak güncelleştirir (değerinin diğer konumda görüntülenmesi de buna dahildir).

> [!NOTE]
> Temsilciye parametre eklemek için [bkz.](creating-and-configuring-type-members.md#create-members)

> [!NOTE]
> Yıkıcı üyesi bir yöntem olmasına karşın, parametrelere sahip olamaz.

### <a name="to-add-a-parameter-to-a-method"></a>Bir yönteme parametre eklemek için

1. Diyagram yüzeyinde, parametre eklemek istediğiniz yöntemi içeren türe tıklayın.

     Tür, Sınıf **Ayrıntıları** penceresinde odaklama ve içeriğini görüntüler.

2. Sınıf **Ayrıntıları** penceresinde, parametre eklemek istediğiniz yöntemin satırını genişletin.

     Yalnızca bir çift parantez içeren girintili parametre satırı görüntülenir ve sözcükler ** \<parametre> ekler.**

3. ** \<parametre>ekle'yi **tıklatın, yeni parametrenin adını yazın ve **Enter**tuşuna basın.

     Yönteme ve yöntemin koduna yeni parametre eklenir. **Sınıf Ayrıntıları** penceresinde ve Özellikler penceresinde görüntülenir.

4. İsteğe bağlı olarak, parametreyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Bir yönteme isteğe bağlı parametre eklemek için

1. Diyagram yüzeyinde, isteğe bağlı parametre eklemek istediğiniz yöntemi içeren türe tıklayın.

     Tür, Sınıf **Ayrıntıları** penceresinde odaklama ve içeriğini görüntüler.

2. Sınıf **Ayrıntıları** penceresinde, isteğe bağlı parametre eklemek istediğiniz yöntemin satırını genişletin.

     Yalnızca bir çift parantez içeren girintili parametre satırı görüntülenir ve sözcükler ** \<parametre> ekler.**

3. ** \<parametre>ekle'yi **tıklatın, yeni parametrenin adını yazın ve **Enter**tuşuna basın.

     Yönteme ve yöntemin koduna yeni parametre eklenir. **Sınıf Ayrıntıları** penceresinde ve Özellikler penceresinde görüntülenir.

4. Özellikler penceresinde, **İsteğe Bağlı Varsayılan** özellik için bir değer yazın. Bir parametrenin İsteğe Bağlı Varsayılan özelliği ayarlandığında bu parametre isteğe bağlı olur.

    > [!NOTE]
    > İsteğe bağlı parametreler, parametre listesindeki en son parametreler olmalıdır.

## <a name="class-details-usage-notes"></a>Sınıf ayrıntıları kullanım notları

**Sınıf Ayrıntıları** penceresini kullanmak için lütfen aşağıdaki ipuçlarını unutmayın.

### <a name="editable-and-non-editable-cells"></a>Düzenlenebilir ve düzenlenemez hücreler

**Sınıf Ayrıntıları** penceresindeki tüm hücreler birkaç özel durum dışında değiştirilebilir:

- Örneğin, başvurulan bir derlemede bulunduğunda, tüm tür salt okunur. Sınıf Tasarımcısı'nda şekli seçtiğinizde, **Sınıf Ayrıntıları** penceresi ayrıntılarını salt okunur durumda görüntüler.

- Dizin oluşturucular için, ad bilgisi salt okunur ve geri kalanı (tür, değiştirici, özet) düzenlenebilir özelliktedir.

- Tüm genel ler **Sınıf Ayrıntıları** penceresinde salt okunur parametrelere sahiptir. Bir genel parametreyi değiştirmek için kaynak kodunu düzenleyin.

- Genel türde tanımlanan tür parametresinin adı salt okunurdur.

- Bir türün kodu kırıldığında (ayrıştırılamaz), **Sınıf Ayrıntıları** penceresi türün içeriğini salt okunur olarak görüntüler.

### <a name="the-class-details-window-and-source-code"></a>Sınıf Ayrıntıları penceresi ve kaynak kodu

- **Sınıf Ayrıntıları** penceresindeki (veya Sınıf Tasarımcısı) bir şekli sağ tıklatıp ardından Görünüm Kodu'nu tıklatarak kaynak kodunu görüntüleyebilirsiniz. Kaynak kodu dosyası açılır ve seçili öğeye kadar ilerler.

- Kaynak kodunun değiştirilmesi, Sınıf Tasarımcısı'ndaki imza bilgilerinin ve **Sınıf Ayrıntıları** penceresindeki görüntüye hemen yansıtılır. Sınıf **Ayrıntıları** penceresi o anda kapatılırsa, bir sonraki açtığınızda yeni bilgiler görünür.

- Bir türün kodu kırıldığında (ayrıştırılamaz), **Sınıf Ayrıntıları** penceresi yalnızca okunduğu gibi türün içeriğini görüntüler.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde pano işlevi

**Sınıf Ayrıntıları** penceresinden alanları veya satırları kopyalayabilir veya kesebilir ve bunları başka bir türe yapıştırabilirsiniz. Bir satırı ancak salt okunur ise kesebilirsiniz. Satırı yapıştırdığınızda, **Sınıf Ayrıntıları** penceresi çakışmayı önlemek için yeni bir ad (kopyalanan satırın adından türetilmiştir) atar.

## <a name="display-of-read-only-information"></a>Salt okunur bilgilerin görüntülenmesi

Sınıf Tasarımcısı ve **Sınıf Ayrıntıları** penceresi aşağıdaki türleri (ve türlerin üyeleri) görüntüleyebilir:

- Sınıf diyagramı içeren bir proje

- Sınıf diyagramı içeren bir projeden başvurulan proje

- Sınıf diyagramı içeren bir projeden başvurulan derleme

Sonraki iki durum için, başvurulan varlık (bir tür veya üye) temsil ettiği sınıf diyagramında salt okunurdur.

Bir projenin tamamı ya da kısımları (tek tek dosyalar gibi) salt okunur olabilir. Projenin veya dosyalarından birinin salt okunur olduğu en yaygın durumlar, bir kaynak kodu denetiminin altında olduğu (ve kullanıma alınmamış), bir dış derlemede var olduğu veya işletim sisteminin dosyaları salt okunur olarak düşündüğü durumlardır.

**Kaynak Kod Denetimi**

Sınıf diyagramı projede dosya olarak kaydedilen için, Sınıf Tasarımcısı veya **Sınıf Ayrıntıları** penceresinde yaptığınız değişiklikleri kaydetmek için projeyi kullanıma almanız gerekir.

**Salt Okunur Projeler**

Proje, kaynak kodu denetimi dışındaki bir nedenle salt okunur olabilir. Projeyi kapatmak, proje dosyasının üzerine yazılması, değişiklikleri atma (kaydetmeme) veya yakın işlemi iptal etme konusunda soran bir iletişim kutusu görüntüler. Üzerine yazmayı tercih ederseniz proje dosyalarının üzerine yazılır ve okuma/yazma özellikli yapılırlar. Yeni sınıf diyagramı dosyası eklenir.

**Salt Okunur Türleri**

Kaynak kod dosyası salt okunur olan bir türü içeren bir projeyi kaydetmeye çalışırsanız, **Yalnızca Okunur Dosyayı Kaydet** iletişim kutusu görüntülenir ve bu da dosyayı yeni bir ad veya yeni bir konum altında kaydetme veya salt okunur dosyanın üzerine yazma seçeneği sunar. Dosyanın üzerine yazarsanız yeni kopyası artık salt okunur özellikte olmaz.

Bir Kod dosyası sözdizimi hatası içeriyorsa, bu dosyadaki kodu gösteren şekiller söz dizimi hatası düzeltilinceye kadar geçici olarak salt okunur olur. Bu durumdaki şekiller, "Kaynak kodu dosyası ayrıştırma hatası içeriyor" yazılı araç ipucunu gösteren kırmızı bir metin ve kırmızı bir simge görüntüler.

Başka bir proje düğümü nün altında veya başvurulan derleme düğümü altında bulunan başvurulan tür (.NET türü gibi), Sınıf Tasarımcısı tasarım yüzeyinde salt okunur olarak gösterilir. Açık durumda bulunan projede var olan bir yerel tür okuma/yazma özelliklidir ve Sınıf Tasarımcısı'nın tasarım yüzeyindeki şekli de böyle belirtilir.

Dizin leyiciler kodve **Sınıf Ayrıntıları** penceresinde okuma-yazma, ancak dizinleyici adı salt okunur.

Sınıf Tasarımcısı veya **Sınıf Ayrıntıları** penceresini kullanarak kısmi yöntemleri düzenleme yapamazsınız; bunları yeniden kullanmak için Kod Düzenleyicisi kullanmanız gerekir.

Sınıf Tasarımcısı veya **Sınıf Ayrıntıları** penceresini kullanarak yerel C++ kodunu düzenlemeyapamazsınız; yerel C++ kodunu yeniden kullanmak için Kod Düzenleyicisi'ni kullanmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Türleri ve ilişkileri görüntüleme](designing-and-viewing-classes-and-types.md)
- [Sınıfları ve türlerini yeniden düzenleme](refactoring-classes-and-types.md)
