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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590416"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Sınıf Tasarımcısı tür üyeleri oluşturma ve yapılandırma

Bu üyeleri bir sınıf diyagramında türlere ekleyebilir ve bu üyeleri **Sınıf Ayrıntıları** penceresinde yapılandırabilirsiniz:

|**Türüyle**|**İçerebildiği Üyeler**|
|--------------| - |
|örneği|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Enum|üye|
|Arabirim|yöntem, özellik, olay (C# ve Visual Basic için)|
|Soyut Sınıf|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Yapı (C# için Struct)|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Temsilci|parametre|
|Modül (Yalnızca VB)|yöntem, özellik, alan, olay, oluşturucu, sabit|

> [!NOTE]
> Bir özelliğin get ve set erişimcileri ek mantığa gerek duymadığında, otomatik uygulanan özellikleri (yalnızca C#) kullanarak özellik bildirimini daha kısa yapın. Tam imzayı göstermek için, **sınıf diyagramı** menüsünden **üye biçimini değiştir** > **tam imzayı görüntüle**' yi seçin. Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Ortak görevler

|Görev|Destekleyici içerik|
|----------| - |
|**Kullanmaya başlayın:** Tür üyelerini oluşturmadan ve yapılandırmadan önce, **Sınıf Ayrıntıları** penceresini açmanız gerekir.|[sınıf ayrıntıları penceresini açmak](creating-and-configuring-type-members.md#open-the-class-details-window) - <br />- [sınıfı ayrıntıları kullanım notları](creating-and-configuring-type-members.md#class-details-usage-notes)<br />[salt okuma bilgilerinin - görüntüleme](creating-and-configuring-type-members.md#display-of-read-only-information)<br />[sınıf diyagramında ve Sınıf Ayrıntıları penceresinde klavye ve fare kısayollarını](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md) - |
|**Tür üyeleri oluşturma ve değiştirme:** **Sınıf Ayrıntıları** penceresini kullanarak yeni üyeler oluşturabilir, üyeleri değiştirebilir ve bir yönteme parametreler ekleyebilirsiniz.|- [üye oluştur](creating-and-configuring-type-members.md#create-members)<br />- [üye değiştirme türü](creating-and-configuring-type-members.md#modify-type-members)<br />[yöntemlere parametre eklemek](creating-and-configuring-type-members.md#add-parameters-to-methods) - |

## <a name="open-the-class-details-window"></a>Sınıf ayrıntıları penceresini açın

Varsayılan olarak, yeni bir sınıf diyagramı açtığınızda **Sınıf Ayrıntıları** penceresi otomatik olarak görünür. Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme](how-to-add-class-diagrams-to-projects.md)). **Sınıf Ayrıntıları** penceresini aşağıdaki yollarla da açabilirsiniz:

- Diyagramda herhangi bir sınıfa sağ tıklayıp bağlam menüsünü görüntüleyin ve **Sınıf Ayrıntıları**' nı seçin.

- Menü çubuğundan **diğer Windows** > **sınıfı ayrıntılarını** **görüntüle** > seçin.

## <a name="create-members"></a>Üye Oluştur

Üye oluşturmak için aşağıdaki araçlardan herhangi birini kullanabilirsiniz:

- **Sınıf Tasarımcısı**

- **Sınıf Ayrıntıları** penceresi araç çubuğu

- **Sınıf Ayrıntıları** penceresi

> [!NOTE]
> Bu bölümdeki yordamları kullanarak oluşturucular ve yıkıcılar da oluşturabilirsiniz. Lütfen oluşturucuların ve yıkıcıların özel türde Yöntemler olduğunu ve bu nedenle sınıf diyagramı şekillerinin içindeki **Yöntemler** bölmesinde ve **Sınıf Ayrıntıları** penceresi kılavuzunun **Yöntemler** bölümünde göründüğünü göz önünde bulundurun.

> [!NOTE]
> Bir temsilciye ekleyebileceğiniz tek varlık parametredir. " **Sınıf Ayrıntıları** penceresi araç çubuğunu kullanarak üye oluşturma" adlı yordamın bu eylem için geçerli olmadığına unutmayın.

### <a name="create-a-member-using-class-designer"></a>Sınıf Tasarımcısı kullanarak üye oluşturma

1. Üye eklemek istediğiniz türe sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından eklemek istediğiniz üye türünü seçin.

     Yeni bir üye imzası oluşturulur ve türe eklenir. **Sınıf Tasarımcısı**, **Sınıf Ayrıntıları** penceresi veya **Özellikler** penceresinde değiştirebileceğiniz bir varsayılan ad verilir.

2. İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Sınıf Ayrıntıları penceresi araç çubuğunu kullanarak üye oluşturma

1. Diyagram yüzeyinde, üye eklemek istediğiniz türü seçin.

     Tür odağı alır ve içeriği **Sınıf Ayrıntıları** penceresinde görüntülenir.

2. **Sınıf Ayrıntıları** penceresi araç çubuğunda, üstteki simgeye tıklayın ve açılan listeden **yeni \<üye >** ' i seçin.

     İmleç, eklemek istediğiniz üye türü için bir satırdaki **ad** alanına gider. Örneğin, **yeni özellik**' e tıkladıysanız, Imleç **Sınıf Ayrıntıları** penceresinin **Özellikler** bölümünde yeni bir satıra gider.

3. Oluşturmak istediğiniz üyenin adını yazın ve Enter'a basın (ya da başka bir şekilde, örneğin, Sekme tuşuna basarak odağı taşıyın).

     Yeni bir üye imzası oluşturulur ve türe eklenir. Üye artık kodda bulunur ve **Sınıf Tasarımcısı**, **sınıf ayrıntıları** penceresi ve Özellikler penceresi görüntülenir.

4. İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="create-a-member-using-the-class-details-window"></a>Sınıf ayrıntıları penceresini kullanarak üye oluşturma

1. Diyagram yüzeyinde, üye eklemek istediğiniz türü seçin.

     Tür odağı alır ve içeriği **Sınıf Ayrıntıları** penceresinde görüntülenir.

2. **Sınıf Ayrıntıları** penceresinde, eklemek istediğiniz üye türünü içeren bölümde **üye > eklemek\<** ' ye tıklayın. Örneğin, bir alan eklemek istiyorsanız **\<alan ekle >** ' ye tıklayın.

3. Oluşturmak istediğiniz üyenin adını yazın ve Enter'a basın.

     Yeni bir üye imzası oluşturulur ve türe eklenir. Üye artık kodda bulunur ve **Sınıf Tasarımcısı**, **sınıf ayrıntıları** penceresi ve Özellikler penceresi görüntülenir.

4. İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

    > [!NOTE]
    > Ayrıca, üye oluşturmak için klavye kısayollarını kullanabilirsiniz. Daha fazla bilgi için [sınıf diyagramı ve Sınıf Ayrıntıları penceresinde klavye ve fare kısayolları](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)bölümüne bakın.

## <a name="modify-type-members"></a>Tür üyelerini değiştir

Sınıf Tasarımcısı, diyagram görüntülenen türlerin üyelerinde değişiklik yapmanıza olanak sağlar. Sınıf diyagramında görüntülenen ve salt okunur olmayan her türün üyelerini değiştirebilirsiniz. Tasarım yüzeyi, Özellikler penceresi ve **Sınıf Ayrıntıları** penceresinde yerinde Düzenle ' yi kullanarak tür üyelerini değiştirirsiniz.

**Sınıf Ayrıntıları** penceresinde görünen tüm Üyeler sınıf diyagramındaki türlerin üyelerini temsil eder. Dört üye türü vardır: yöntemler, özellikler, alanlar ve olaylar.

Tüm üye satırları, üyeleri türe göre gruplandıran başlıkların altında görünür. Örneğin, tüm özellikler başlık **özellikleri**altında görünür, bu, kılavuzdaki bir düğüm olarak daraltılabilir veya Genişletilebilir.

Her üye satırı aşağıdaki öğeleri görüntüler:

- **Üye simgesi**

     Her üyü türü kendi simgesiyle gösterilir. Üyenin imzasını göstermek için fareyi üye simgesine getirin. Satırı seçmek için, üye simgesine ya da üye simgesinin solundaki boşluğa tıklayın.

- **Üye adı**

     Üye satırındaki **ad** sütunu üyenin adını görüntüler. Bu ad ayrıca Özellikler penceresi **ad** özelliğinde de görüntülenir. Okuma/Yazma izinlerine sahip herhangi bir üyenin adını değiştirmek için bu hücreyi kullanın.

     **Ad** sütunu tam adı göstermek için çok darsa, üye adının yanındaki fare adının tamamı adı görüntüler.

- **Üye türü**

     **MemberType** hücresi IntelliSense kullanır ve bu, geçerli projede veya başvurulan projelerde kullanılabilen tüm türlerin listesinden seçim yapmanızı sağlar.

- **Üye değiştiricisi**

     Üyenin görünürlük değiştiricisini `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected Friend` (`protected internal`) veya `Default`olarak değiştirin.

- **\<üye Ekle >**

     **Sınıf Ayrıntıları** penceresindeki son satır, **ad** hücresine **üye > eklemek\<** metni içerir. Bu hücreye tıklarsanız yeni bir üye oluşturabilirsiniz. Daha fazla bilgi için bkz. [üyeleri oluşturma](creating-and-configuring-type-members.md#create-members).

- **Özellikler penceresi üye özellikleri**

     **Sınıf Ayrıntıları** penceresi, Özellikler penceresi görüntülenen üye özelliklerinin bir alt kümesini görüntüler. Özelliğin bir konumda değiştirilmesi, özelliğin değerini global olarak güncelleştirir. Değerinin diğer konumda görüntülenmesi de buna dahildir.

- **Özet**

     **Özet** hücresi, üye hakkında bilgilerin bir özetini gösterir. **Özet hücresinde,** üyenin **Özeti**, **dönüş türü**ve **açıklamalar** hakkındaki bilgileri görüntülemek veya düzenlemek için bu üç noktaya tıklayın.

- **Gizlenecek**

     **Gizle** onay kutusu seçildiğinde, üye tür içinde görüntülenmez.

### <a name="to-modify-a-type-member"></a>Bir tür üyesini değiştirmek için

1. Sınıf Tasarımcısı'nı kullanarak bir tür seçin.

2. **Sınıf Ayrıntıları** penceresi görüntülenmiyorsa, sınıf Tasarımcısı araç çubuğunda **Sınıf Ayrıntıları** penceresi düğmesine tıklayın.

3. **Sınıf Ayrıntıları** penceresi kılavuzunun alanlarındaki değerleri düzenleyin. Her düzenlemeden sonra ENTER'a basın ya da bir başka yolla, örneğin SEKME tuşuna basarak, odağı düzenlenen alanın dışına taşıyın. Düzenlemeleriniz anında koda yansır.

    > [!NOTE]
    > Bir üyenin yalnızca adını değiştirmek istiyorsanız, bunu yerinde düzenlemeyi kullanarak yapabilirsiniz.

## <a name="add-parameters-to-methods"></a>Yöntemlere parametreler ekleme

**Sınıf Ayrıntıları** penceresini kullanarak yöntemlere parametreler ekleyin. Parametreler, zorunlu veya isteğe bağlı olacak şekilde yapılandırılabilir. Bir parametresinin **Isteğe bağlı varsayılan** özelliği için bir değer sağlamak, tasarımcı 'nın isteğe bağlı bir parametre olarak kod oluşturmasını söyler.

Parametre satırı aşağıdaki öğeleri içerir:

- **Ad**

     Bir parametre satırındaki **ad** sütunu, parametrenin adını görüntüler. Bu ad ayrıca Özellikler penceresi **ad** özelliğinde de görüntülenir. Okuma/Yazma izinlerine sahip herhangi bir parametrenin adını değiştirmek için bu hücreyi kullanabilirsiniz.

     **Ad** sütunu tam adı göstermek için çok dar ise parametre adının üzerine gelindiğinde parametrenin adı görüntülenir.

- **Türüyle**

     **Parametre türü** hücresi IntelliSense kullanır, bu, geçerli projede veya başvurulan projelerde kullanılabilen tüm türlerin listesinden seçim yapmanızı sağlar.

- **İcisi**

     Bir parametre satırındaki **değiştirici** hücresi kabul eder ve parametrenin yeni değiştiricisini görüntüler. Yeni bir C#parametre değiştiricisi girmek için, açılan liste kutusunu, içindeki **none**, **ref**, **Out**veya **params** ÖĞESINDEN, ve **ByVal**, **ByRef**veya **ParamArray** ' de vb. arasından seçim yapmak için kullanın.

- **Özet**

     Bir parametre satırındaki **Özet** hücresi, kod düzenleyicisine parametre girerken IntelliSense 'de görünen kod açıklamalarının girilmesine izin verir.

- **\<parametre ekleme >**

     Bir üyenin son parametre satırı, **ad** hücresinde **\>Add parametre <** metni içerir. Bu hücreye tıklanması yeni bir parametre oluşturmanıza izin verir. Daha fazla bilgi için, bkz. [bir yönteme parametre eklemek için](creating-and-configuring-type-members.md#add-parameters-to-methods).

**Özellikler** penceresi, **Sınıf Ayrıntıları** penceresinde görüntülenen aynı parametre özelliklerini görüntüler: **ad**, **tür**, **değiştirici**, **Özet**ve **isteğe bağlı varsayılan** özellik. Özelliğin bir konumda değiştirilmesi, özelliğin değerini global olarak güncelleştirir (değerinin diğer konumda görüntülenmesi de buna dahildir).

> [!NOTE]
> Bir temsilciye bir parametre eklemek için bkz. [üyeleri oluşturma](creating-and-configuring-type-members.md#create-members).

> [!NOTE]
> Yıkıcı üyesi bir yöntem olmasına karşın, parametrelere sahip olamaz.

### <a name="to-add-a-parameter-to-a-method"></a>Bir yönteme parametre eklemek için

1. Diyagram yüzeyinde, parametre eklemek istediğiniz yöntemi içeren türe tıklayın.

     Tür, odağı ve içeriğini edinir **Sınıf Ayrıntıları** penceresinde görüntüler.

2. **Sınıf Ayrıntıları** penceresinde, parametre eklemek istediğiniz yöntemin satırını genişletin.

     Yalnızca bir çift ayraçları ve **\<parametresi ekle >** sözcüklerini içeren girintili bir parametre satırı görünür.

3. **\<parametre ekle >** ' ye tıklayın, yeni parametrenin adını yazın ve **ENTER**tuşuna basın.

     Yeni parametre yöntemine ve yöntemin koduna eklenir. **Sınıf Ayrıntıları** penceresinde ve Özellikler penceresi görüntülenir.

4. İsteğe bağlı olarak, parametreyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Bir yönteme isteğe bağlı parametre eklemek için

1. Diyagram yüzeyinde, isteğe bağlı parametre eklemek istediğiniz yöntemi içeren türe tıklayın.

     Tür, odağı ve içeriğini edinir **Sınıf Ayrıntıları** penceresinde görüntüler.

2. **Sınıf Ayrıntıları** penceresinde, isteğe bağlı parametre eklemek istediğiniz yöntemin satırını genişletin.

     Yalnızca bir çift ayraçları ve **\<parametresi ekle >** sözcüklerini içeren girintili bir parametre satırı görünür.

3. **\<parametre ekle >** ' ye tıklayın, yeni parametrenin adını yazın ve **ENTER**tuşuna basın.

     Yeni parametre yöntemine ve yöntemin koduna eklenir. **Sınıf Ayrıntıları** penceresinde ve Özellikler penceresi görüntülenir.

4. Özellikler penceresi, **Isteğe bağlı varsayılan** özellik için bir değer yazın. Bir parametrenin İsteğe Bağlı Varsayılan özelliği ayarlandığında bu parametre isteğe bağlı olur.

    > [!NOTE]
    > İsteğe bağlı parametreler, parametre listesindeki en son parametreler olmalıdır.

## <a name="class-details-usage-notes"></a>Sınıf Ayrıntıları kullanım notları

**Sınıf Ayrıntıları** penceresini kullanmak için aşağıdaki ipuçlarına göz önünde olun.

### <a name="editable-and-non-editable-cells"></a>Düzenlenebilir ve düzenlenemez hücreler

**Sınıf Ayrıntıları** penceresindeki tüm hücreler birkaç özel durum ile düzenlenebilir:

- Bütün tür salt okunurdur, örneğin, başvurulan bir derlemede yer alır. Sınıf Tasarımcısı şekli seçtiğinizde, **Sınıf Ayrıntıları** penceresi ayrıntılarını salt okuma durumunda görüntüler.

- Dizin oluşturucular için, ad bilgisi salt okunur ve geri kalanı (tür, değiştirici, özet) düzenlenebilir özelliktedir.

- Tüm genel türler, **Sınıf Ayrıntıları** penceresinde salt okuma parametrelerine sahiptir. Bir genel parametreyi değiştirmek için kaynak kodunu düzenleyin.

- Genel türde tanımlanan tür parametresinin adı salt okunurdur.

- Bir türün kodu bozuk (çözümlenemez) olduğunda, **Sınıf Ayrıntıları** penceresi türün içeriğini salt okuma olarak görüntüler.

### <a name="the-class-details-window-and-source-code"></a>Sınıf Ayrıntıları penceresi ve kaynak kodu

- Kaynak kodunu, **Sınıf Ayrıntıları** penceresinde (veya sınıf Tasarımcısı) bir şekle sağ tıklayıp ardından kodu görüntüle ' ye tıklayarak görebilirsiniz. Kaynak kodu dosyası açılır ve seçili öğeye kadar ilerler.

- Kaynak kodunu değiştirmek, Sınıf Tasarımcısı ve **Sınıf Ayrıntıları** penceresindeki imza bilgilerinin görüntüsüne hemen yansıtılır. **Sınıf Ayrıntıları** penceresi saatte kapatılırsa yeni bilgiler, bir dahaki sefer açıldığında görünür.

- Bir türün kodu bozuk (çözümlenemez) olduğunda, **Sınıf Ayrıntıları** penceresi türün içeriğini salt okuma olarak görüntüler.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde Pano işlevselliği

**Sınıf Ayrıntıları** penceresinden alanları veya satırları kopyalayabilir veya kesebilir ve bunları başka bir türe yapıştırabilirsiniz. Bir satırı ancak salt okunur ise kesebilirsiniz. Satırı yapıştırdığınızda, **Sınıf Ayrıntıları** penceresi bir çakışmayı önlemek için yeni bir ad (kopyalanmış satırın adından türetilir) atar.

## <a name="display-of-read-only-information"></a>Salt okuma bilgilerini görüntüleme

Sınıf Tasarımcısı ve **Sınıf Ayrıntıları** penceresi aşağıdakiler için türleri (ve türlerin üyelerini) gösterebilir:

- Sınıf diyagramı içeren bir proje

- Sınıf diyagramı içeren bir projeden başvurulan proje

- Sınıf diyagramı içeren bir projeden başvurulan derleme

Sonraki iki durum için, başvurulan varlık (bir tür veya üye) temsil ettiği sınıf diyagramında salt okunurdur.

Bir projenin tamamı ya da kısımları (tek tek dosyalar gibi) salt okunur olabilir. Projenin veya dosyalarından birinin salt okunur olduğu en yaygın durumlar, bir kaynak kodu denetiminin altında olduğu (ve kullanıma alınmamış), bir dış derlemede var olduğu veya işletim sisteminin dosyaları salt okunur olarak düşündüğü durumlardır.

**Kaynak kodu denetimi**

Bir sınıf diyagramı bir projede dosya olarak kaydedildiğinden, Sınıf Tasarımcısı veya **Sınıf Ayrıntıları** penceresinde yaptığınız değişiklikleri kaydetmek için projeyi kullanıma almanız gerekir.

**Salt okuma projeleri**

Proje, kaynak kodu denetimi dışındaki bir nedenle salt okunur olabilir. Projeyi kapatmak, proje dosyasının üzerine yazılıp yazılmayacağını, değişiklikleri atmayı (kaydetme) veya kapatma işlemini iptal etmeyi soran bir iletişim kutusu görüntüler. Üzerine yazmayı tercih ederseniz proje dosyalarının üzerine yazılır ve okuma/yazma özellikli yapılırlar. Yeni sınıf diyagramı dosyası eklenir.

**Salt okuma türleri**

Kaynak kodu dosyası salt okunan bir tür içeren bir projeyi kaydetmeye çalışırsanız, dosyayı yeni bir adla veya yeni bir konuma kaydetme ya da salt yazılır dosyanın üzerine yazma seçimlerini sağlayan **salt yazılır dosyayı kaydet** iletişim kutusu görüntülenir. Dosyanın üzerine yazarsanız yeni kopyası artık salt okunur özellikte olmaz.

Bir Kod dosyası sözdizimi hatası içeriyorsa, bu dosyadaki kodu gösteren şekiller söz dizimi hatası düzeltilinceye kadar geçici olarak salt okunur olur. Bu durumdaki şekiller, "Kaynak kodu dosyası ayrıştırma hatası içeriyor" yazılı araç ipucunu gösteren kırmızı bir metin ve kırmızı bir simge görüntüler.

Başka bir proje düğümü altında ya da başvurulan bir derleme düğümü altında bulunan başvurulan bir tür (.NET türü gibi), Sınıf Tasarımcısı tasarım yüzeyinde salt okunurdur. Açık durumda bulunan projede var olan bir yerel tür okuma/yazma özelliklidir ve Sınıf Tasarımcısı'nın tasarım yüzeyindeki şekli de böyle belirtilir.

Dizin oluşturucular kodda ve **Sınıf Ayrıntıları** penceresinde okuma-yazma, ancak dizin oluşturucu adı salt okunurdur.

Kısmi yöntemleri Sınıf Tasarımcısı veya **Sınıf Ayrıntıları** penceresini kullanarak düzenleyemezsiniz; bunları düzenlemek için kod düzenleyicisini kullanmanız gerekir.

Sınıf Tasarımcısı veya C++ **Sınıf Ayrıntıları** penceresini kullanarak yerel kodu düzenleyemezsiniz; Yerel C++ kodu düzenlemek Için kod düzenleyicisini kullanmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Türleri ve ilişkileri görüntüleme](designing-and-viewing-classes-and-types.md)
- [Sınıfları ve türleri yeniden düzenleme](refactoring-classes-and-types.md)
