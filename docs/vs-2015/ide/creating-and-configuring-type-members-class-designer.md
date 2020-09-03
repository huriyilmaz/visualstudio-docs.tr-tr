---
title: Tür üyeleri oluşturma ve yapılandırma (Sınıf Tasarımcısı) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b871c406b0a2b36d1e7f02a070ab1052510ed20b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619228"
---
# <a name="creating-and-configuring-type-members-class-designer"></a>Tür Üyeleri Oluşturma ve Yapılandırma (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu üyeleri bir sınıf diyagramında türlere ekleyebilir ve bu üyeleri **Sınıf Ayrıntıları** penceresinde yapılandırabilirsiniz:

|**Tür**|**İçerebildiği Üyeler**|
|--------------|--------------------------------|
|Sınıf|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Sabit listesi|üye|
|Arabirim|yöntem, özellik, olay (C# ve Visual Basic için)|
|Soyut Sınıf|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Yapı (C# için Struct)|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Temsilci|Parametre|
|Modül (Yalnızca VB)|yöntem, özellik, alan, olay, oluşturucu, sabit|

> [!NOTE]
> Bir özelliğin get ve set erişimcileri ek mantığa gerek duymadığında, otomatik uygulanan özellikleri (yalnızca C#) kullanarak özellik bildirimini daha kısa yapın. Tam imzayı göstermek için, **sınıf diyagramı** menüsünde, **üye biçimini değiştir**' i seçin, **tam imzayı görüntüleyin**. Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7).

## <a name="common-tasks"></a>Ortak Görevler

|Görev|Destekleyici İçerik|
|----------|------------------------|
|**Kullanmaya başlayın:** Tür üyelerini oluşturmadan ve yapılandırmadan önce, sınıf ayrıntıları penceresini açmanız gerekir.|-   [Sınıf Detayları Penceresi açma](../ide/creating-and-configuring-type-members-class-designer.md#OpenClassDetails)<br />-   [Sınıf Ayrıntıları kullanım notları](../ide/creating-and-configuring-type-members-class-designer.md#ClassDetailsUsageNotes)<br />-   [Salt okuma bilgilerini görüntüleme](../ide/creating-and-configuring-type-members-class-designer.md#ReadOnlyInfo)<br />-   [Sınıf diyagramında ve Sınıf Detayları Penceresi Klavye ve fare kısayolları (Sınıf Tasarımcısı)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md)|
|**Tür üyeleri oluşturma ve değiştirme:** Sınıf ayrıntıları penceresini kullanarak yeni üyeler oluşturabilir, üyeleri değiştirebilir ve bir yönteme parametreler ekleyebilirsiniz.|-   [Üyeler oluşturuluyor](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)<br />-   [Tür üyelerini değiştirme](../ide/creating-and-configuring-type-members-class-designer.md#ModifyTypeMembers)<br />-   [Yöntemlere parametreler ekleme](../ide/creating-and-configuring-type-members-class-designer.md#AddMethodParams)|

## <a name="opening-the-class-details-window"></a><a name="OpenClassDetails"></a> Sınıf Detayları Penceresi açma
 Varsayılan olarak, yeni bir sınıf diyagramını açtığınızda Sınıf Detayları Penceresi otomatik olarak görünür (bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme (sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)). Ayrıca, aşağıdaki yollarla, Sınıf Ayrıntıları penceresini doğrudan da açabilirsiniz.

#### <a name="to-open-the-class-details-window"></a>Sınıf Ayrıntıları penceresini açmak için

1. Bağlam menüsünü göstermek için diyagramdaki herhangi bir sınıfa sağ tıklayın.

2. Bağlam menüsünde **sınıf detayları penceresi**' ye tıklayın.

   – veya -

- Görünüm menüsünde **diğer pencereler** ' in üzerine gelin ve ardından **Sınıf Ayrıntıları**' na tıklayın.

## <a name="creating-members"></a><a name="CreateMembers"></a> Üyeler oluşturuluyor
 Üye oluşturmak için aşağıdaki araçlardan herhangi birini kullanabilirsiniz:

- Sınıf Tasarımcısı

- Sınıf Ayrıntıları penceresi araç çubuğu

- Sınıf Ayrıntıları penceresi

> [!NOTE]
> Bu bölümdeki yordamları kullanarak oluşturucular ve yıkıcılar da oluşturabilirsiniz. Lütfen oluşturucuların ve yıkıcıların özel türde Yöntemler olduğunu ve bu nedenle sınıf diyagramı şekillerinin içindeki **Yöntemler** bölmesinde ve Sınıf Ayrıntıları penceresi kılavuzunun **Yöntemler** bölümünde göründüğünü göz önünde bulundurun.

> [!NOTE]
> Bir temsilciye ekleyebileceğiniz tek varlık parametredir. 'Sınıf Ayrıntıları Penceresi araç çubuğunu kullanarak üye oluşturmak için' başlıklı yordamın bu eylem için geçerli olmadığını unutmayın.

#### <a name="to-create-a-member-using-class-designer"></a>Sınıf Tasarımcısı'nı kullanarak üye oluşturmak için

1. Üye eklemek istediğiniz türe sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından eklemek istediğiniz üye türünü seçin.

     Yeni bir üye imzası oluşturulur ve türe eklenir. **Sınıf Tasarımcısı**, **Sınıf Ayrıntıları** penceresi veya **Özellikler** penceresinde değiştirebileceğiniz bir varsayılan ad verilir.

2. İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

#### <a name="to-create-a-member-using-the-class-details-window-toolbar"></a>Sınıf Ayrıntıları Penceresi araç çubuğunu kullanarak üye oluşturmak için

1. Diyagram yüzeyinde, üye eklemek istediğiniz türü seçin.

     Tür odağa gelir ve içeriği Sınıf Ayrıntıları penceresinde görüntülenir.

2. Sınıf Ayrıntıları penceresi araç çubuğunda en üstteki simgesine tıklayın ve açılan listeden **Yeni \<member> ** ' yi seçin.

     İmleç, eklemek istediğiniz üye türü için bir satırdaki **ad** alanına gider. Örneğin, **yeni özellik**' e tıkladıysanız, Imleç sınıf ayrıntıları penceresinin **Özellikler** bölümünde yeni bir satıra gider.

3. Oluşturmak istediğiniz üyenin adını yazın ve Enter'a basın (ya da başka bir şekilde, örneğin, Sekme tuşuna basarak odağı taşıyın).

     Yeni bir üye imzası oluşturulur ve türe eklenir. Üye artık kodda bulunur ve **Sınıf Tasarımcısı**, Sınıf Ayrıntıları penceresi ve Özellikler penceresi görüntülenir.

4. İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

#### <a name="to-create-a-member-using-the-class-details-window"></a>Sınıf Ayrıntıları Penceresini kullanarak üye oluşturmak için

1. Diyagram yüzeyinde, üye eklemek istediğiniz türü seçin.

     Tür odağa gelir ve içeriği Sınıf Ayrıntıları penceresinde görüntülenir.

2. Sınıf Ayrıntıları penceresinde, eklemek istediğiniz üye türünü içeren bölümde, ' ye tıklayın **\<add member>** . Örneğin, bir alan eklemek istiyorsanız, öğesine tıklayın **\<add field>** .

3. Oluşturmak istediğiniz üyenin adını yazın ve Enter'a basın.

     Yeni bir üye imzası oluşturulur ve türe eklenir. Üye artık kodda bulunur ve **Sınıf Tasarımcısı**, Sınıf Ayrıntıları penceresi ve Özellikler penceresi görüntülenir.

4. İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

     **Note:** Ayrıca, üye oluşturmak için klavye kısayollarını kullanabilirsiniz. Daha fazla bilgi için bkz. [sınıf diyagramında klavye ve fare kısayolları ve sınıf detayları penceresi (sınıf Tasarımcısı)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md).

## <a name="modifying-type-members"></a><a name="ModifyTypeMembers"></a> Tür üyelerini değiştirme
 Sınıf Tasarımcısı, diyagram görüntülenen türlerin üyelerinde değişiklik yapmanıza olanak sağlar. Sınıf diyagramında görüntülenen ve salt okunur olmayan her türün üyelerini değiştirebilirsiniz. (Bkz. [salt okuma bilgilerini görüntüleme (sınıf Tasarımcısı)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Tasarım yüzeyi, Özellikler penceresi ve Sınıf Ayrıntıları penceresinde yerinde Düzenle ' yi kullanarak tür üyelerini değiştirirsiniz.

 Sınıf Ayrıntıları penceresinde görüntülenen tüm üyeler sınıf diyagramındaki türlerin üyelerini temsil eder. Dört üye türü vardır: yöntemler, özellikler, alanlar ve olaylar.

 Tüm üye satırları, üyeleri türe göre gruplandıran başlıkların altında görünür. Örneğin, tüm özellikler başlık **özellikleri**altında görünür, bu, kılavuzdaki bir düğüm olarak daraltılabilir veya Genişletilebilir.

 Her üye satırı aşağıdaki öğeleri görüntüler:

- **Üye simgesi**

     Her üyü türü kendi simgesiyle gösterilir. Üyenin imzasını görüntülemek için fareyi üye simgesinin üzerine getirin. Satırı seçmek için, üye simgesine ya da üye simgesinin solundaki boşluğa tıklayın.

- **Üye adı**

     Üye satırındaki **ad** sütunu üyenin adını görüntüler. Bu ad ayrıca Özellikler penceresi **ad** özelliğinde de görüntülenir. Okuma/Yazma izinlerine sahip herhangi bir üyenin adını değiştirmek için bu hücreyi kullanın.

     **Ad** sütunu tam adı göstermek için çok darsa, üye adının yanındaki fare adının tamamı adı görüntüler.

- **Üye Türü**

     **MemberType** hücresi IntelliSense kullanır ve bu, geçerli projede veya başvurulan projelerde kullanılabilen tüm türlerin listesinden seçim yapmanızı sağlar.

- **Üye değiştiricisi**

     Üyenin görünürlük değiştiricisini `Public` ( `public` ), `Private` ( `private` ), `Friend` ( `internal` ) `Protected` ( `protected` ), `Protected``Friend` ( `protected``internal` ) veya `Default` ile değiştirin.

- **\<add member>**

     Sınıf Ayrıntıları penceresindeki son satır, **\<add member>** **ad** hücresindeki metni içerir. Bu hücreye tıklarsanız yeni bir üye oluşturabilirsiniz. Daha fazla bilgi için bkz. [üyeleri oluşturma](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).

- **Özellikler penceresi üye özellikleri**

     Sınıf Ayrıntıları penceresi, Özellikler penceresinde görüntülenen üye özelliklerinin bir alt kümesini görüntüler. Özelliğin bir konumda değiştirilmesi, özelliğin değerini global olarak güncelleştirir. Değerinin diğer konumda görüntülenmesi de buna dahildir.

- **Özet**

     **Özet** hücresi, üye hakkında bilgilerin bir özetini gösterir. **Özet hücresinde,** üyenin **Özeti**, **dönüş türü**ve **açıklamalar** hakkındaki bilgileri görüntülemek veya düzenlemek için bu üç noktaya tıklayın.

- **Gizle**

     **Gizle** onay kutusu seçildiğinde, üye tür içinde görüntülenmez.

#### <a name="to-modify-a-type-member"></a>Bir tür üyesini değiştirmek için

1. Sınıf Tasarımcısı'nı kullanarak bir tür seçin.

2. Sınıf Ayrıntıları penceresi görüntülenmiyorsa, Sınıf Tasarımcısı araç çubuğunda **sınıf detayları penceresi** düğmesine tıklayın.

3. Sınıf Ayrıntıları penceresi kılavuzunun alanlarındaki değerleri düzenleyin. Her düzenlemeden sonra ENTER'a basın ya da bir başka yolla, örneğin SEKME tuşuna basarak, odağı düzenlenen alanın dışına taşıyın. Düzenlemeleriniz anında koda yansır.

    > [!NOTE]
    > Bir üyenin yalnızca adını değiştirmek istiyorsanız, bunu yerinde düzenlemeyi kullanarak yapabilirsiniz.

## <a name="adding-parameters-to-methods"></a><a name="AddMethodParams"></a> Yöntemlere parametreler ekleme
 Sınıf Ayrıntıları penceresini kullanarak yöntemlere parametreler ekleyin. Parametreler, zorunlu veya isteğe bağlı olacak şekilde yapılandırılabilir. Bir parametresinin **Isteğe bağlı varsayılan** özelliği için bir değer sağlamak, tasarımcı 'nın isteğe bağlı bir parametre olarak kod oluşturmasını söyler.

 Parametre satırı aşağıdaki öğeleri içerir:

- **Ad**

   Bir parametre satırındaki **ad** sütunu, parametrenin adını görüntüler. Bu ad ayrıca Özellikler penceresi **ad** özelliğinde de görüntülenir. Okuma/Yazma izinlerine sahip herhangi bir parametrenin adını değiştirmek için bu hücreyi kullanabilirsiniz.

   **Ad** sütunu tam adı göstermek için çok dar ise parametre adının üzerine gelindiğinde parametrenin adı görüntülenir.

- **Tür**

   **Parametre türü** hücresi IntelliSense kullanır, bu, geçerli projede veya başvurulan projelerde kullanılabilen tüm türlerin listesinden seçim yapmanızı sağlar.

- **İcisi**

   Bir parametre satırındaki **değiştirici** hücresi kabul eder ve parametrenin yeni değiştiricisini görüntüler. Yeni bir parametre değiştiricisi girmek için, açılan liste kutusunu kullanarak C# ' de **none**, **ref**, **Out**veya **params** arasından seçim yapın ve vb 'de **ByVal**, **ByRef**veya **ParamArray** ' i seçin.

- **Özet**

   Bir parametre satırındaki **Özet** hücresi, kod düzenleyicisine parametre girerken IntelliSense 'de görünen kod açıklamalarının girilmesine izin verir.

- **\<add parameter>**

   Bir üyenin son parametre satırı, **ad** hücresine **<Add parametresi \> ** metin içerir. Bu hücreye tıklanması yeni bir parametre oluşturmanıza izin verir. Daha fazla bilgi için, bkz. [bir yönteme parametre eklemek için](../ide/creating-and-configuring-type-members-class-designer.md#HowToAddParameterToMethod).

  **Özellikler penceresi parametre özellikleri**

  Özellikler penceresi, Sınıf Ayrıntıları penceresinde görüntülenen aynı parametre özelliklerini görüntüler: **ad**, **tür**, **değiştirici**, **Özet**ve **isteğe bağlı varsayılan** özellik. Özelliğin bir konumda değiştirilmesi, özelliğin değerini global olarak güncelleştirir (değerinin diğer konumda görüntülenmesi de buna dahildir).

> [!NOTE]
> Bir temsilciye bir parametre eklemek için bkz. [üyeleri oluşturma](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).

> [!NOTE]
> Yıkıcı üyesi bir yöntem olmasına karşın, parametrelere sahip olamaz.

### <a name="to-add-a-parameter-to-a-method"></a><a name="HowToAddParameterToMethod"></a> Bir yönteme parametre eklemek için

1. Diyagram yüzeyinde, parametre eklemek istediğiniz yöntemi içeren türe tıklayın.

     Tür odağa gelir ve içeriği Sınıf Ayrıntıları penceresinde görüntülenir.

2. Sınıf Ayrıntıları penceresinde, parametre eklemek istediğiniz yöntemin satırını genişletin.

     Yalnızca bir parantez ve sözcük çifti içeren girintili bir parametre satırı görünür ** \<add parameter> .**

3. Tıklayın **\<add parameter>** , yeni parametrenin adını yazın ve **ENTER**tuşuna basın.

     Yeni parametre yönteme ve yöntemin koduna eklenir. Sınıf Ayrıntıları penceresinde ve Özellikler penceresinde görünür.

4. İsteğe bağlı olarak, parametreyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Bir yönteme isteğe bağlı parametre eklemek için

1. Diyagram yüzeyinde, isteğe bağlı parametre eklemek istediğiniz yöntemi içeren türe tıklayın.

     Tür odağa gelir ve içeriği Sınıf Ayrıntıları penceresinde görüntülenir.

2. Sınıf Ayrıntıları penceresinde, isteğe bağlı parametre eklemek istediğiniz yöntemin satırını genişletin.

     Yalnızca bir parantez ve sözcük çifti içeren girintili bir parametre satırı görünür ** \<add parameter> .**

3. Tıklayın **\<add parameter>** , yeni parametrenin adını yazın ve **ENTER**tuşuna basın.

     Yeni parametre yönteme ve yöntemin koduna eklenir. Sınıf Ayrıntıları penceresinde ve Özellikler penceresinde görünür.

4. Özellikler penceresi, **Isteğe bağlı varsayılan** özellik için bir değer yazın. Bir parametrenin İsteğe Bağlı Varsayılan özelliği ayarlandığında bu parametre isteğe bağlı olur.

    > [!NOTE]
    > İsteğe bağlı parametreler, parametre listesindeki en son parametreler olmalıdır.

## <a name="class-details-usage-notes"></a><a name="ClassDetailsUsageNotes"></a> Sınıf Ayrıntıları kullanım notları
 Sınıf Ayrıntıları penceresinin kullanımına ilişkin aşağıdaki ipuçlarına dikkat edin.

 **Düzenlenebilir ve düzenlenemez hücreler**

 Bir kaç özel durum dışında, Sınıf Ayrıntıları penceresindeki tüm hücreler düzenlenebilir:

- Bütün tür salt okunurdur, örneğin, başvurulan bir derlemede yer alır (bkz. [salt okuma bilgilerini görüntüleme (sınıf Tasarımcısı)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Sınıf Tasarımcısı şekli seçtiğinizde, Sınıf Ayrıntıları penceresi ayrıntılarını salt okuma durumunda görüntüler.

- Dizin oluşturucular için, ad bilgisi salt okunur ve geri kalanı (tür, değiştirici, özet) düzenlenebilir özelliktedir.

- Tüm genel öğeler Sınıf Ayrıntıları penceresinde salt okunur parametrelere sahiptir. Bir genel parametreyi değiştirmek için kaynak kodunu düzenleyin.

- Genel türde tanımlanan tür parametresinin adı salt okunurdur.

- Türün kodu bozuk (çözümlenemez) olduğunda, Sınıf Ayrıntıları penceresi türün içeriğini salt okunur olarak görüntüler.

  **Sınıf Detayları Penceresi ve kaynak kodu**

- Kaynak kodunu, Sınıf Ayrıntıları (veya Sınıf Tasarımcısı) penceresinde bir şekle sağ tıklayıp ardından Kodu Görüntüle'ye tıklayarak görüntüleyebilirsiniz. Kaynak kodu dosyası açılır ve seçili öğeye kadar ilerler.

- Kaynak kodunun değiştirilmesi, Sınıf Tasarımcısı ve Sınıf Ayrıntıları penceresinde imza bilgilerinin görüntüsüne anında yansıtılır. Sınıf Ayrıntıları penceresi bu sırada kapalıysa, pencereyi bir sonraki açışınızda yeni bilgiler görülür.

- Türün kodu bozuk (çözümlenemez) olduğunda, Sınıf Ayrıntıları penceresi türün içeriğini salt okunur olarak görüntüler.

  **Sınıf Detayları Penceresi Pano işlevselliği**

  Sınıf Ayrıntıları penceresinden alanları veya satırları kopyalayabilir ya da kesebilir ve bunları başka bir türe yapıştırabilirsiniz. Bir satırı ancak salt okunur ise kesebilirsiniz. Satırı yapıştırdığınızda, Sınıf Ayrıntıları penceresi çakışma olmasını önlemek için yeni bir ad (kopyalanan satırın adından türetilir) atar.

## <a name="display-of-read-only-information"></a><a name="ReadOnlyInfo"></a> Salt okuma bilgilerini görüntüleme
 Sınıf Tasarımcısı ve Sınıf Ayrıntıları penceresi aşağıdaki öğeler için türleri (ve türlerin üyelerini) görüntüleyebilir:

- Sınıf diyagramı içeren bir proje

- Sınıf diyagramı içeren bir projeden başvurulan proje

- Sınıf diyagramı içeren bir projeden başvurulan derleme

  Sonraki iki durum için, başvurulan varlık (bir tür veya üye) temsil ettiği sınıf diyagramında salt okunurdur.

  Bir projenin tamamı ya da kısımları (tek tek dosyalar gibi) salt okunur olabilir. Projenin veya dosyalarından birinin salt okunur olduğu en yaygın durumlar, bir kaynak kodu denetiminin altında olduğu (ve kullanıma alınmamış), bir dış derlemede var olduğu veya işletim sisteminin dosyaları salt okunur olarak düşündüğü durumlardır.

  **Kaynak kodu denetimi**

  Sınıf diyagramı projenin içine bir dosya olarak kaydedildiğinden, Sınıf Tasarımcısı veya Sınıf Ayrıntıları penceresinde yaptığınız değişiklikleri kaydetmek için projeyi kullanıma almanız gerekir.

  **Salt okuma projeleri**

  Proje, kaynak kodu denetimi dışındaki bir nedenle salt okunur olabilir. Proje kapatıldığında, proje dosyasının üzerine mi yazılacağını, değişikliklerin yok mu sayılacağını(kaydetme) ya da kapatma işleminin iptal mi edileceğini soran bir iletişim kutusu görüntülenir. Üzerine yazmayı tercih ederseniz proje dosyalarının üzerine yazılır ve okuma/yazma özellikli yapılırlar. Yeni sınıf diyagramı dosyası eklenir.

  **Salt okuma türleri**

  Kaynak kodu dosyası salt okunan bir tür içeren bir projeyi kaydetmeye çalışırsanız, dosyayı yeni bir adla veya yeni bir konuma kaydetme ya da salt yazılır dosyanın üzerine yazma seçimlerini sağlayan **salt yazılır dosyayı kaydet** iletişim kutusu görüntülenir. Dosyanın üzerine yazarsanız yeni kopyası artık salt okunur özellikte olmaz.

  Bir Kod dosyası sözdizimi hatası içeriyorsa, bu dosyadaki kodu gösteren şekiller söz dizimi hatası düzeltilinceye kadar geçici olarak salt okunur olur. Bu durumdaki şekiller, "Kaynak kodu dosyası ayrıştırma hatası içeriyor" yazılı araç ipucunu gösteren kırmızı bir metin ve kırmızı bir simge görüntüler.

  Başka bir proje düğümü altında ya da başvurulan bir derleme düğümü altında bulunan bir başvurulan tür (.NET Framework türü gibi), Sınıf Tasarımcısı'nın tasarım yüzeyinde salt okunur olarak belirtilir. Açık durumda bulunan projede var olan bir yerel tür okuma/yazma özelliklidir ve Sınıf Tasarımcısı'nın tasarım yüzeyindeki şekli de böyle belirtilir.

  Dizin oluşturucular kod içinde ve Sınıf Ayrıntıları penceresinde okuma/yazma özelliklidir, ancak dizin oluşturucunun adı salt okunurdur.

  Kısmi yöntemleri Sınıf Tasarımcısı veya Sınıf Ayrıntıları penceresini kullanarak düzenleyemezsiniz; bunları düzenlemek için Kod Düzenleyicisi'ni kullanmanız gerekir.

  Yerel C++ kodunu Sınıf Tasarımcısı veya Sınıf Ayrıntıları penceresini kullanarak düzenleyemezsiniz; yerel C++ kodunu düzenlemek için Kod Düzenleyicisi'ni kullanmanız gerekir.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Türleri ve İlişkilendirmeleri Görüntüleme (Sınıf Tasarımcısı)](../ide/viewing-types-and-relationships-class-designer.md)|Varolan türlerinizi, üyelerinizi ve ilişkilerinizi bir sınıf diyagramında görüntüleyebilirsiniz.|
|[Sınıfları ve Türleri Yeniden Düzenleme (Sınıf Tasarımcısı)](../ide/refactoring-classes-and-types-class-designer.md)|Yeniden düzenlemeyi kullanarak türü ve tür üyelerini kolayca yeniden adlandırabilirsiniz. Ayrıca, sınıflar arasında üye taşıyabilir, bir sınıfı kısmi sınıflara bölebilir ve arabirimler uygulayabilirsiniz.|