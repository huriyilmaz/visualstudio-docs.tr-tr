---
title: Tür Üyeleri Oluşturma ve Yapılandırma (Sınıf Tasarımcısı)
description: Sınıf diyagramında türlere üye eklemeyi ve bu üyeleri Sınıf Ayrıntıları penceresinde yapılandırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: c8626486389be4a0d5fbc7cf1a5696cec6bfa798854e8d78e796e6e5f475f2bc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121373474"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Sınıf Tasarımcısı'de tür üyeleri oluşturma ve yapılandırma

Bu üyeleri bir sınıf diyagramında türlere ekleyebilir ve bu üyeleri Sınıf Ayrıntıları **penceresinde yapılandırabilirsiniz:**

|**Tür**|**Içerenin üyeler**|
|--------------| - |
|Sınıf|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Sabit listesi|üye|
|Arabirim|yöntem, özellik, olay (C# ve Visual Basic için)|
|Soyut Sınıf|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Yapı (C# için Struct)|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Temsilci|parametre|
|Modül (Yalnızca VB)|yöntem, özellik, alan, olay, oluşturucu, sabit|

> [!NOTE]
> Bir özelliğin get ve set erişimcileri ek mantığa gerek duymadığında, otomatik uygulanan özellikleri (yalnızca C#) kullanarak özellik bildirimini daha kısa yapın. Tam imzayı göstermek için Sınıf Diyagramı menüsünde **Üyeleri Değiştir** Biçimi Tam **İmzayı**  >  **Görüntüle'yi seçin.** Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz. [Otomatik Uygulanan Özellikler.](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties)

## <a name="common-tasks"></a>Genel görevler

|Görev|destek içeriği|
|----------| - |
|**Kullanmaya başlayın:** Tür üyelerini oluşturmadan ve yapılandırmadan önce Sınıf Ayrıntıları **penceresini açabilirsiniz.**|- [Sınıf Ayrıntıları penceresini açın](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Sınıf Ayrıntıları kullanım notları](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Salt okunur bilgilerin görüntüsü](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Sınıf Diyagramı ve Sınıf Ayrıntıları penceresinde klavye ve fare kısayolları](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Tür üyelerini oluşturma ve değiştirme:** Sınıf Ayrıntıları penceresini kullanarak yeni üyeler oluşturabilir, üyeleri değiştirebilir ve bir yönteme **parametre ebilirsiniz.**|- [Üye oluşturma](creating-and-configuring-type-members.md#create-members)<br />- [Tür üyelerini değiştirme](creating-and-configuring-type-members.md#modify-type-members)<br />- [Yöntemlere parametre ekleme](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Sınıf Ayrıntıları penceresini açın

Varsayılan olarak, **yeni bir sınıf** diyagramını a açmak için Sınıf Ayrıntıları penceresi otomatik olarak görünür. Bkz. [Nasıl yapabilirsiniz: Projelere sınıf diyagramları ekleme](how-to-add-class-diagrams-to-projects.md)). Sınıf Ayrıntıları penceresini **aşağıdaki yollarla** da açabilirsiniz:

- Bir bağlam menüsünü görüntülemek için diyagramda herhangi bir sınıfa sağ tıklayın ve Ardından Sınıf **Ayrıntıları'ı seçin.**

- Menü   >  **çubuğundan Diğer Windows** Sınıf  >  **Ayrıntılarını** Görüntüle'yi seçin.

## <a name="create-members"></a>Üye oluşturma

Üye oluşturmak için aşağıdaki araçlardan herhangi birini kullanabilirsiniz:

- **Sınıf Tasarımcısı**

- **Sınıf Ayrıntıları pencere** araç çubuğu

- **Sınıf Ayrıntıları** penceresi

> [!NOTE]
> Bu bölümdeki yordamları kullanarak oluşturucular ve yıkıcılar da oluşturabilirsiniz. Oluşturucuların ve yok etmelerin özel yöntem türleri olduğunu ve bu nedenle bunların  sınıf diyagramı şekillerinin Yöntemler bölmesinde  ve Sınıf Ayrıntıları pencere kılavuzunda Yöntemler bölümünde gösterildiğini **unutmayın.**

> [!NOTE]
> Bir temsilciye ekleyebileceğiniz tek varlık parametredir. 'Sınıf Ayrıntıları pencere araç çubuğunu kullanarak  üye oluşturmak için' başlıklı yordamın bu eylem için geçerli olmadığını unutmayın.

### <a name="create-a-member-using-class-designer"></a>Sınıf Tasarımcısı kullanarak üye oluşturma

1. Üye eklemek istediğiniz türe sağ tıklayın, Ekle'nin üzerine **gelin** ve eklemek istediğiniz üye türünü seçin.

     Yeni bir üye imzası oluşturulur ve türe eklenir. Bu, Sınıf Tasarımcısı, **Sınıf Ayrıntıları** penceresinde veya Özellikler **penceresinde** değiştirebilirsiniz varsayılan bir **ad** verilir.

2. İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Sınıf Ayrıntıları pencere araç çubuğunu kullanarak üye oluşturma

1. Diyagram yüzeyinde, üye eklemek istediğiniz türü seçin.

     Tür odağı elde ediyor ve içeriği Sınıf Ayrıntıları **penceresinde** görüntülenir.

2. Sınıf Ayrıntıları **penceresi araç** çubuğunda üst simgeye tıklayın ve açılan **listeden \<member>** Yeni'yi seçin.

     İmleç, **eklemek** istediğiniz üyenin tür için bir satırdaki Ad alanına taşınır. Örneğin, Yeni **Özellik'e tıklarsanız,** imleci Sınıf Ayrıntıları penceresinin **Özellikler** bölümünde yeni bir **satıra** taşır.

3. Oluşturmak istediğiniz üyenin adını yazın ve Enter'a basın (ya da başka bir şekilde, örneğin, Sekme tuşuna basarak odağı taşıyın).

     Yeni bir üye imzası oluşturulur ve türe eklenir. Üye artık kodda mevcuttur ve **Sınıf Tasarımcısı,** Sınıf **Ayrıntıları penceresinde** ve Özellikler penceresi.

4. İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="create-a-member-using-the-class-details-window"></a>Sınıf Ayrıntıları penceresini kullanarak üye oluşturma

1. Diyagram yüzeyinde, üye eklemek istediğiniz türü seçin.

     Tür odağı elde ediyor ve içeriği Sınıf Ayrıntıları **penceresinde** görüntülenir.

2. Sınıf **Ayrıntıları penceresinde,** eklemek istediğiniz üyenin tür içeren bölümünde'ye **\<add member>** tıklayın. Örneğin, bir alan eklemek için **\<add field>** tıklayın.

3. Oluşturmak istediğiniz üyenin adını yazın ve Enter'a basın.

     Yeni bir üye imzası oluşturulur ve türe eklenir. Üye artık kodda mevcuttur ve **Sınıf Tasarımcısı,** Sınıf **Ayrıntıları penceresinde** ve Özellikler penceresi.

4. İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

    > [!NOTE]
    > Üye oluşturmak için klavye kısayollarını da kullanabilirsiniz. Daha fazla bilgi için Sınıf [Diyagramı ve Sınıf Ayrıntıları penceresindeki Klavye ve Fare Kısayolları'ne bakın.](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)

## <a name="modify-type-members"></a>Tür üyelerini değiştirme

Sınıf Tasarımcısı, diyagram görüntülenen türlerin üyelerinde değişiklik yapmanıza olanak sağlar. Sınıf diyagramında görüntülenen ve salt okunur olmayan her türün üyelerini değiştirebilirsiniz. Tasarım yüzeyinde, tasarım yüzeyinde ve Sınıf Ayrıntıları penceresinde Özellikler penceresi düzenleyerek tür **üyelerini değiştirirsiniz.**

Sınıf Ayrıntıları penceresinde görüntülenen **tüm üyeler,** sınıf diyagramında türlerin üyelerini temsil ediyor. Dört üye türü vardır: yöntemler, özellikler, alanlar ve olaylar.

Tüm üye satırları, üyeleri türe göre gruplandıran başlıkların altında görünür. Örneğin, tüm özellikler, **kılavuzda** bir düğüm olarak daraltılmış veya genişletilen Özellikler başlığı altında görünür.

Her üye satırı aşağıdaki öğeleri görüntüler:

- **Üye Simgesi**

     Her üyü türü kendi simgesiyle gösterilir. Üyenin imzasını görüntülemek için fareyi üye simgesine işaret ettirin. Satırı seçmek için, üye simgesine ya da üye simgesinin solundaki boşluğa tıklayın.

- **Üye Adı**

     Üye **satırdaki** Ad sütunu, üyenin adını görüntüler. Bu ad, dosyanın **Name** özelliğinde de Özellikler penceresi. Okuma/Yazma izinlerine sahip herhangi bir üyenin adını değiştirmek için bu hücreyi kullanın.

     Ad **sütunu** adın tamamını göstermek için çok darsa, fareyi üye adına işaret etmek adın tamamını görüntüler.

- **Üye Türü**

     **MemberType hücresi,** geçerli projede veya başvurulan projelerde kullanılabilen tüm türler listesinden seçimnizi sağlayan IntelliSense'i kullanır.

- **Üye Değiştiricisi**

     Bir üyenin görünürlük değiştiricisini `Public` ( `public` ), ( ), ( `Private` ) ( ), ( ) veya olarak `private` `Friend` `internal` `Protected` `protected` `Protected Friend` `protected internal` `Default` değiştirir.

- **\<add member>**

     Sınıf Ayrıntıları penceresindeki **son satır,** Ad **\<add member>** hücresinde **metni** içerir. Bu hücreye tıklarsanız yeni bir üye oluşturabilirsiniz. Daha fazla bilgi için [bkz. Üye oluşturma.](creating-and-configuring-type-members.md#create-members)

- **Özellikler penceresi'daki üye özellikleri**

     Sınıf **Ayrıntıları** penceresi, üye özelliklerinin bir alt kümesini görüntüler ve Özellikler penceresi. Özelliğin bir konumda değiştirilmesi, özelliğin değerini global olarak güncelleştirir. Değerinin diğer konumda görüntülenmesi de buna dahildir.

- **Özet**

     Özet **hücresi,** üyeyle ilgili bilgilerin özetini ortaya çıkarır. Özet, Dönüş Türü ve **Üyenin** Açıklamalar bilgilerini görüntülemek veya düzenlemek için **Özet** hücresinde **üç nokta** tıklayın.

- **Gizle**

     Gizle **onay** kutusu seçildiğinde üye türünde görüntülenmez.

### <a name="to-modify-a-type-member"></a>Bir tür üyesini değiştirmek için

1. Sınıf Tasarımcısı'nı kullanarak bir tür seçin.

2. Sınıf **Ayrıntıları penceresi** görüntülenmezse, araç **çubuğundaki** Sınıf Ayrıntıları Sınıf Tasarımcısı tıklayın.

3. Sınıf Ayrıntıları pencere kılavuzu **alanlarındaki değerleri** düzenleyin. Her düzenlemeden sonra ENTER'a basın ya da bir başka yolla, örneğin SEKME tuşuna basarak, odağı düzenlenen alanın dışına taşıyın. Düzenlemeleriniz anında koda yansır.

    > [!NOTE]
    > Bir üyenin yalnızca adını değiştirmek istiyorsanız, bunu yerinde düzenlemeyi kullanarak yapabilirsiniz.

## <a name="add-parameters-to-methods"></a>Yöntemlere parametre ekleme

Sınıf Ayrıntıları penceresini kullanarak **yöntemlere parametreler** ekleyin. Parametreler, zorunlu veya isteğe bağlı olacak şekilde yapılandırılabilir. Bir parametrenin İsteğe **Bağlı Varsayılan** özelliği için bir değer sağlamak tasarımcıya isteğe bağlı parametre olarak kod oluşturma talimatı verir.

Parametre satırı aşağıdaki öğeleri içerir:

- **Ad**

     Parametre **satırdaki** Name sütunu parametrenin adını görüntüler. Bu ad, dosyanın **Name** özelliğinde de Özellikler penceresi. Okuma/Yazma izinlerine sahip herhangi bir parametrenin adını değiştirmek için bu hücreyi kullanabilirsiniz.

     Name sütunu adın tamamını göstermek için çok  darsa parametre adına işaret etmek parametrenin adını görüntüler.

- **Tür**

     Parametre **Türü hücresi,** geçerli projede veya başvurulan projelerde kullanılabilen tüm türler listesinden seçimnizi sağlayan IntelliSense'i kullanır.

- **Değiştirici**

     Parametre **satırdaki** Değiştirici hücresi parametrenin yeni değiştiricisini kabul eder ve görüntüler. Yeni bir parametre değiştiricisi girmek için açılan liste kutusunu kullanarak Hiçbiri **,** **ref**, **out** veya **C# içinde params** ve VB içinde **ByVal**, **ByRef** veya **ParamArray'i** seçin.

- **Özet**

     Parametre **satırdaki** Özet hücresi, parametreyi kod düzenleyicisine girerken IntelliSense'te görünen kod açıklamalarının girisine olanak sağlar.

- **\<add parameter>**

     Bir üyenin son parametre satırı, Name **<\> parametre eklemek için** gerekli **metni** içerir. Bu hücreye tıklanması yeni bir parametre oluşturmanıza izin verir. Daha fazla bilgi için [bkz. Yöntemine parametre eklemek için.](creating-and-configuring-type-members.md#add-parameters-to-methods)

Özellikler **penceresi,** Sınıf Ayrıntıları penceresinde görüntülenen aynı parametre özelliklerini **görüntüler:** **Ad,** **Tür,** **Değiştirici,** Özet **ve** İsteğe Bağlı **Varsayılan** özelliği. Özelliğin bir konumda değiştirilmesi, özelliğin değerini global olarak güncelleştirir (değerinin diğer konumda görüntülenmesi de buna dahildir).

> [!NOTE]
> Bir temsilciye parametre eklemek için bkz. [Üye oluşturma.](creating-and-configuring-type-members.md#create-members)

> [!NOTE]
> Yıkıcı üyesi bir yöntem olmasına karşın, parametrelere sahip olamaz.

### <a name="to-add-a-parameter-to-a-method"></a>Bir yönteme parametre eklemek için

1. Diyagram yüzeyinde, parametre eklemek istediğiniz yöntemi içeren türe tıklayın.

     Tür odağı elde ediyor ve içeriği Sınıf Ayrıntıları **penceresinde görüntüleniyor.**

2. Sınıf **Ayrıntıları penceresinde,** parametre eklemek istediğiniz yöntemin satırını genişletin.

     Yalnızca bir çift parantez ve sözcük içeren girintili parametre satırı **\<add parameter> görüntülenir.**

3. 'a **\<add parameter>** tıklayın, yeni parametrenin adını yazın ve Enter tuşuna **basın.**

     yeni parametresi yöntemine ve yönteminin koduna eklenir. Sınıf Ayrıntıları penceresinde **ve** Özellikler penceresi.

4. İsteğe bağlı olarak, parametreyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Bir yönteme isteğe bağlı parametre eklemek için

1. Diyagram yüzeyinde, isteğe bağlı parametre eklemek istediğiniz yöntemi içeren türe tıklayın.

     Tür odağı elde ediyor ve içeriği Sınıf Ayrıntıları **penceresinde görüntüleniyor.**

2. Sınıf **Ayrıntıları penceresinde,** isteğe bağlı parametre eklemek istediğiniz yöntemin satırı genişletin.

     Yalnızca bir çift parantez ve sözcük içeren girintili parametre satırı **\<add parameter> görüntülenir.**

3. 'a **\<add parameter>** tıklayın, yeni parametrenin adını yazın ve Enter tuşuna **basın.**

     yeni parametresi yöntemine ve yönteminin koduna eklenir. Sınıf Ayrıntıları penceresinde **ve** Özellikler penceresi.

4. Aşağıdaki Özellikler penceresi İsteğe Bağlı Varsayılan özelliği **için bir değer** yazın. Bir parametrenin İsteğe Bağlı Varsayılan özelliği ayarlandığında bu parametre isteğe bağlı olur.

    > [!NOTE]
    > İsteğe bağlı parametreler, parametre listesindeki en son parametreler olmalıdır.

## <a name="class-details-usage-notes"></a>Sınıf ayrıntıları kullanım notları

Sınıf Ayrıntıları penceresini kullanmaya ilişkin aşağıdaki **ipuçlarına dikkat** edin.

### <a name="editable-and-non-editable-cells"></a>Düzenlenebilir ve düzenlenemez hücreler

Sınıf Ayrıntıları **penceresindeki tüm** hücreler birkaç özel durum dışında düzenlenebilir:

- Örneğin, başvurulan bir derlemede yer alan tür salt okunur olur. Görünümde şekli Sınıf Tasarımcısı, **Sınıf Ayrıntıları** penceresi ayrıntılarını salt okunur durumda görüntüler.

- Dizin oluşturucular için, ad bilgisi salt okunur ve geri kalanı (tür, değiştirici, özet) düzenlenebilir özelliktedir.

- Tüm genel türler, Sınıf Ayrıntıları penceresinde salt okunur **parametrelere** sahip olur. Bir genel parametreyi değiştirmek için kaynak kodunu düzenleyin.

- Genel türde tanımlanan tür parametresinin adı salt okunurdur.

- Bir türün kodu bozuk olduğunda (ayrılamaz), **Sınıf Ayrıntıları** penceresi türün içeriğini salt okunur olarak görüntüler.

### <a name="the-class-details-window-and-source-code"></a>Sınıf Ayrıntıları penceresi ve kaynak kodu

- Sınıf Ayrıntıları penceresinde bir şekle sağ  tıklar (veya Sınıf Tasarımcısı) ve ardından Kodu Görüntüle'ye tıklayarak kaynak kodu görüntüebilirsiniz. Kaynak kodu dosyası açılır ve seçili öğeye kadar ilerler.

- Kaynak kodun değiştirilmesi, Sınıf Tasarımcısı ve Sınıf Ayrıntıları penceresinde imza bilgileri **görüntüleniyor.** Sınıf **Ayrıntıları penceresi** o sırada kapatılırsa, yeni bilgiler bir sonraki açılacak şekilde görünür.

- Bir türün kodu bozuk olduğunda (ayrılamaz), **Sınıf Ayrıntıları** penceresi türün içeriğini salt okunur olarak görüntüler.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde pano işlevi

Sınıf Ayrıntıları penceresinden alanları veya satırları kopyalayıp **kesebilirsiniz** ve bunları başka bir türe yapıştırabilirsiniz. Bir satırı ancak salt okunur ise kesebilirsiniz. Satırı yapıştırdığınız sırada, **Sınıf Ayrıntıları** penceresi çakışmayı önlemek için yeni bir ad (kopyalanan satırın adı türetilen) atar.

## <a name="display-of-read-only-information"></a>Salt okunur bilgilerin görüntüsü

Sınıf Tasarımcısı ve Sınıf **Ayrıntıları** penceresi, aşağıdakiler için türleri (ve türlerin üyelerini) görüntüler:

- Sınıf diyagramı içeren bir proje

- Sınıf diyagramı içeren bir projeden başvurulan proje

- Sınıf diyagramı içeren bir projeden başvurulan derleme

Sonraki iki durum için, başvurulan varlık (bir tür veya üye) temsil ettiği sınıf diyagramında salt okunurdur.

Bir projenin tamamı ya da kısımları (tek tek dosyalar gibi) salt okunur olabilir. Projenin veya dosyalarından birinin salt okunur olduğu en yaygın durumlar, bir kaynak kodu denetiminin altında olduğu (ve kullanıma alınmamış), bir dış derlemede var olduğu veya işletim sisteminin dosyaları salt okunur olarak düşündüğü durumlardır.

**Kaynak Kodu Denetimi**

Sınıf diyagramı bir projeye dosya olarak kaydedildikleri için, projesinde veya Sınıf Ayrıntıları penceresinde yaptığınız değişiklikleri kaydetmek Sınıf Tasarımcısı **projeyi denetlemeniz** gerekir.

**Salt Okunur Projeler**

Proje, kaynak kodu denetimi dışındaki bir nedenle salt okunur olabilir. Projenin kapatılması, proje dosyasının üzerine yazma, değişiklikleri atma (kaydetme) veya kapatma işlemini iptal etme sorularını soran bir iletişim kutusu görüntüler. Üzerine yazmayı tercih ederseniz proje dosyalarının üzerine yazılır ve okuma/yazma özellikli yapılırlar. Yeni sınıf diyagramı dosyası eklenir.

**Salt Okunur Türler**

Kaynak kodu dosyası salt okunur olan bir tür içeren bir projeyi  kaydetmeyi denersanız, dosyayı yeni bir ad veya yeni bir konum altına kaydetme veya salt okunur dosyanın üzerine yazma seçenekleri veren Read-Only Dosyasını Kaydet iletişim kutusu görüntülenir. Dosyanın üzerine yazarsanız yeni kopyası artık salt okunur özellikte olmaz.

Bir Kod dosyası sözdizimi hatası içeriyorsa, bu dosyadaki kodu gösteren şekiller söz dizimi hatası düzeltilinceye kadar geçici olarak salt okunur olur. Bu durumdaki şekiller, "Kaynak kodu dosyası ayrıştırma hatası içeriyor" yazılı araç ipucunu gösteren kırmızı bir metin ve kırmızı bir simge görüntüler.

Başka bir proje düğümü altında ya da başvurulan bir derleme düğümü altında bulunan başvurulan bir tür (.NET türü gibi), Sınıf Tasarımcısı tasarım yüzeyinde salt okunurdur. Açık durumda bulunan projede var olan bir yerel tür okuma/yazma özelliklidir ve Sınıf Tasarımcısı'nın tasarım yüzeyindeki şekli de böyle belirtilir.

Dizin oluşturucular kodda ve **Sınıf Ayrıntıları** penceresinde okuma-yazma, ancak dizin oluşturucu adı salt okunurdur.

Kısmi yöntemleri Sınıf Tasarımcısı veya **Sınıf Ayrıntıları** penceresini kullanarak düzenleyemezsiniz; bunları düzenlemek için kod düzenleyicisini kullanmanız gerekir.

Sınıf Tasarımcısı veya **Sınıf Ayrıntıları** penceresini kullanarak yerel C++ kodunu düzenleyemezsiniz; Yerel C++ kodunu düzenlemek için kod düzenleyicisini kullanmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Türleri ve ilişkileri görüntüleme](designing-and-viewing-classes-and-types.md)
- [Sınıfları ve türleri yeniden düzenleme](refactoring-classes-and-types.md)
