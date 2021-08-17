---
title: 'Yeni Project Oluşturma: Başlık Altında, Bölüm 1 | Microsoft Docs'
description: Kendi proje türünüz (Bölüm 1/2) Visual Studio tümleşik geliştirme ortamında (IDE) neler olduğunu ayrıntılı bir şekilde göz atabilirsiniz.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 308ed373ecfbecf29702a338ac6a595775c29d2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063206"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Yeni Proje Oluşturma: Arka Plan, 1. Bölüm
Hiç kendi proje türlerinizi oluşturma hakkında düşünceniz oldu mu? Yeni bir proje oluşturmanın ne olduğunu merak ediyor musunuz? Şimdi perdenin altına göz atalım ve neler olduğunu göreceğiz.

 Sizin için koordinatlar Visual Studio görevler vardır:

- Kullanılabilir tüm proje türlerinden bir ağaç görüntüler.

- Her proje türü için uygulama şablonlarının listesini görüntüler ve birini seçmenizi sağlar.

- Uygulama için proje adı ve yol gibi proje bilgilerini toplar.

- Bu bilgileri proje fabrikasına iletir.

- Geçerli çözümde proje öğeleri ve klasörleri oluşturur.

## <a name="the-new-project-dialog-box"></a>Yeni Project İletişim Kutusu
 Her şey yeni bir proje için bir proje türü seçerek başlar. İlk olarak Dosya menüsündeki **Yeni Project'a** **tıklayın.** Yeni **Project** iletişim kutusu aşağıdaki gibi görünür:

 ![Yeni Proje iletişim kutusunun ekran görüntüsü.](../../extensibility/internals/media/newproject.gif)

 Şimdi bunlara daha yakından bakalım. Project **türleri** ağacı, oluştur oluştur oluştura çeşitli proje türlerini listeler. **Visual C#** Windows gibi bir proje türü Windows başlamaya başlamaya yardımcı olacak uygulama şablonlarının listesini görüntülenir. **Visual Studio şablonlar,** Visual Studio tarafından yüklenir ve bilgisayarınızın herhangi bir kullanıcısı tarafından kullanılabilir. Oluştursanız veya toplayan yeni şablonlar **Şablonlarım'a eklenebilir** ve yalnızca sizin için kullanılabilir.

 Windows Uygulaması gibi **bir** şablon seçerek iletişim kutusunda uygulama türünün açıklaması görüntülenir; bu durumda, **kullanıcı arabirimine sahip bir uygulama oluşturmaya Windows projesidir.**

 Yeni Veri Project **iletişim** kutusunun en altında, daha fazla bilgi top eden çeşitli denetimler görüntülenir. Gördüğünüz denetimler proje türüne bağlıdır, ancak genellikle  proje Adı metin kutusu,  **Konum** metin kutusu  ve ilgili Gözat düğmesi ile Çözüm Adı metin kutusu ve çözüm için dizin oluştur onay **kutusu** içerir.

## <a name="populating-the-new-project-dialog-box"></a>Yeni Dosya İletişim Project Doldurmak
 Yeni **Project** iletişim kutusu bilgilerini nereden alıyor? Burada iki mekanizma vardır ve bunlardan biri kullanım dışıdır. Yeni **Project** iletişim kutusu, her iki mekanizmadan alınan bilgileri birleştirir ve görüntüler.

 Eski (kullanım dışı) yöntemi, sistem kayıt defteri girdilerini ve .vsdir dosyalarını kullanır. Bu mekanizma, bir Visual Studio çalışır. Daha yeni yöntem .vstemplate dosyalarını kullanır. Bu mekanizma, Visual Studio, örneğin çalıştırarak başlatılırken çalışır

```
devenv /setup
```

 veya

```
devenv /installvstemplates
```

### <a name="project-types"></a>Proje Türleri
 Visual **C#** **ve Diğer Project** gibi kök düğüm türlerine sahip düğümlerin konumu ve adları sistem kayıt defteri girdileri tarafından belirlenir.  Veritabanı ve Akıllı Cihaz gibi  alt düğümlerin **organizasyonu,** karşılık gelen .vstemplate dosyalarını içeren klasörlerin hiyerarşisini yansıtıyor. Önce kök düğümlere bakalım.

#### <a name="project-type-root-nodes"></a>Project Tür Kök Düğümleri
 Başlatılırken, sistem kayıt defteri anahtarının alt anahtarlarını HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs türler ağacının kök [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **düğümlerini derlemek ve Project olur.** Bu bilgiler daha sonra kullanmak üzere önbelleğe alınmış olur. TemplateDirs \\ {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 anahtarına bakın. Her giriş bir VSPackage GUID'idir. Alt anahtarın adı (/1) yoksayılır, ancak varlığı bunun kök düğüm **Project olduğunu** gösterir. Kök düğüm, ağaç türleri ağacında görünümünü kontrol etmek için birkaç alt **anahtara Project sahip** olabilir. Şimdi bazılarına göz atacağız.

##### <a name="default"></a>(Varsayılan)
 Bu, kök düğümü adlaştıran yerelleştirilmiş dizenin kaynak kimliğidir. Dize kaynağı VSPackage GUID'si tarafından seçilen uydu DLL'sinde bulunur.

 Örnekte VSPackage GUID'si şu şekildedir:

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 ve kök düğümün (/1) kaynak kimliği (varsayılan değer) #2345

 Yakındaki Paketler anahtarında GUID'yi bulup SatelliteDll alt anahtarını incelersiniz, dize kaynağını içeren derlemenin yolunu bulabilirsiniz:

 \<Visual Studio installation path>\VC#\VCSPackages\1033\csprojui.dll

 Bunu doğrulamak için, Dosya Gezgini açın ve csprojui.dll Visual Studio dizinine sürükleyin. Dize tablosu, kaynak kaynak #2345 Visual C# açıklamalı **alt yazısını gösterir.**

##### <a name="sortpriority"></a>SortPriority
 Bu, kök düğümün Project **belirler.**

 SortPriority REG_DWORD 0x00000014 (20)

 Öncelik sayısı ne kadar düşük ise ağaçtaki konum o kadar yüksek olur.

##### <a name="developeractivity"></a>DeveloperActivity
 Bu alt anahtar varsa, kök düğümün konumu Geliştirici Hesabı iletişim Ayarlar denetlenr. Örneğin,

 DeveloperActivity REG_SZ VC #

 , geliştirme için ayarlanmışsa Visual C# Visual Studio düğüm olacağını [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] gösterir. Aksi takdirde, Diğer Diller'in bir **alt düğümü olur.**

##### <a name="folder"></a>Klasör
 Bu alt anahtar varsa, kök düğüm belirtilen klasörün alt düğümü olur. Anahtarın altında olası klasörlerin listesi görüntülenir

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 Örneğin, Veritabanı Projeleri girdisi, PseudoFolders'daki Diğer Project Türleri girdisi ile eşleşen bir Klasör anahtarına sahip. Bu nedenle, **Project türleri** ağacında, **Veritabanı** Projeleri Diğer Proje Türleri'nin bir alt **Project olur.**

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Project Alt Düğümler ve .vstdir Dosyaları Yazın
 Project türleri ağacında alt  düğümlerin konumu, ProjectTemplates klasörlerinde klasörlerin hiyerarşisini izler. Makine şablonları (**Visual Studio** şablonlar) için tipik konum \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ ve kullanıcı şablonları **(** Şablonlarım) için tipik konum \Belgelerim\Visual Studio 14.0\Templates\ProjectTemplates konumundadır. \\ Bu iki konumdaki klasör hiyerarşileri, veri türleri ağacını oluşturmak **Project birleştirilir.**

 C# Visual Studio ayarlarıyla ilgili ayrıntılar için Project **türleri** ağacı aşağıdakine benzer:

 ![C# Project ile Visual Studio türler klasör ağacının ekran görüntüsü.](../../extensibility/internals/media/projecttypes.png)

 Karşılık gelen ProjectTemplates klasörü şöyle görünür:

 ![C# Project ile Visual Studio Şablonlar klasör ağacının ekran görüntüsü.](../../extensibility/internals/media/projecttemplates.png)

 Yeni **Project** iletişim kutusu açıldığında ProjectTemplates klasöründen geçiş yapın ve yapısını Project değişikliklerle birlikte yeniden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oluşturur: 

- Uygulama türü ağacının **Project düğümü** uygulama şablonu tarafından belirlenir.

- Düğüm adı yerelleştirilmiş olabilir ve özel karakterler içerebilir.

- Sıralama düzeni değiştirilebilir.

##### <a name="finding-the-root-node-for-a-project-type"></a>Bir Etki Alanı Türü için Project Bulma
 ProjectTemplates Visual Studio çapraz geçişler olduğunda, tüm .zip dosyaları açar ve .vstemplate dosyalarını ayıklar. .vstemplate dosyası, bir uygulama şablonunu açıklamak için XML kullanır. Daha fazla bilgi için [bkz. Yeni Project Oluşturma: Başlık Altında, Bölüm İki](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Etiket, \<ProjectType> uygulamanın proje türünü belirler. Örneğin, \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip dosyası şu etikete sahip bir EmptyProject.vstemplate dosyası içerir:

```
<ProjectType>CSharp</ProjectType>
```

 ProjectTemplates klasöründeki alt klasör değil etiketi, uygulamanın kök düğümünü Project \<ProjectType> **belirler.** Örnekte, Windows CE uygulamaları **Visual C#** kök düğümü altında görünür ve WindowsCE klasörünü VisualBasic klasörüne taşısanız bile Windows CE uygulamaları Yine de **Visual C#** kök düğümü altında görünür.

##### <a name="localizing-the-node-name"></a>Düğüm Adını Yerelleştirme
 ProjectTemplates Visual Studio geçişleri olduğunda, bulduğu tüm .vstdir dosyalarını inceler. .vstdir dosyası, Yeni dosya iletişim kutusundaki proje türünün görünümünü Project **xml** dosyasıdır. .vstdir dosyasında, düğüm türü \<LocalizedName> düğümünü Project **kullanın.**

 Örneğin, \CSharp\Database\TemplateIndex.vstdir dosyası şu etiketi içerir:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Bu, kök düğüme (bu durumda Veritabanı) ad verir yerelleştirilmiş dizenin uydu DLL'sini ve kaynak kimliğini **belirler.** Yerelleştirilmiş ad, .NET gibi klasör adları için kullanılabilir durumda olan özel **karakterler içerebilir.**

 Etiket \<LocalizedName> yoksa proje türü, klasörün kendisi tarafından **smartPhone2003 olarak adlandırılmıştır.**

##### <a name="finding-the-sort-order-for-a-project-type"></a>Project türü için sıralama düzenini bulma
 Proje türünün sıralama düzenini öğrenmek için. vstdir dosyaları \<SortOrder> etiketini kullanır.

 örneğin, \csharp\ Windows \ Windows. vstdir dosyası şu etiketi içerir:

```
<SortOrder>5</SortOrder>
```

 \Csharp\bir Templateındex.vstdir dosyasında daha büyük bir değer içeren bir etiket vardır:

```
<SortOrder>5000</SortOrder>
```

 etiketteki sayının sayısı \<SortOrder> arttıkça, ağaç içindeki konum daha yüksektir, bu nedenle **Windows** düğümü **Project types** ağacındaki **veritabanı** düğümünden daha yüksek görünür.

 \<SortOrder>Proje türü için etiket belirtilmemişse, belirtim içeren tüm proje türlerini izleyen alfabetik sırada görünür \<SortOrder> .

 Belgelerim (**Şablonlarım**) klasörlerinde. vstdir dosyaları olmadığını unutmayın. Kullanıcı uygulaması proje türü adları yerelleştirilmez ve alfabetik sırada görünür.

#### <a name="a-quick-review"></a>Hızlı bir gözden geçirme
 **yeni Project** iletişim kutusunu değiştirelim ve yeni bir kullanıcı projesi şablonu oluşturalım.

1. \program Files \ Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\CSharp klasörüne bir myprojectnode alt klasörü ekleyin.

2. Herhangi bir metin düzenleyicisini kullanarak MyProjectNode klasöründe MyProject. vstdir dosyasını oluşturun.

3. Bu satırları. vstdir dosyasına ekleyin:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. . Vstdir dosyasını kaydedin ve kapatın.

5. Herhangi bir metin düzenleyicisini kullanarak MyProjectNode klasöründe MyProject. vstemplate dosyasını oluşturun.

6. Bu satırları. vstemplate dosyasına ekleyin:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. . Vstemplate dosyasını kaydedin ve düzenleyiciyi kapatın.

8. . Vstemplate dosyasını yeni bir sıkıştırılmış MyProjectNode\MyProject.zip klasörüne gönderin.

9. Visual Studio komut penceresinde, şunu yazın:

    ```
    devenv /installvstemplates
    ```

   Visual Studio'yu açın.

10. **yeni Project** iletişim kutusunu açın ve **Visual C#** proje düğümünü genişletin.

    ![genişletilmiş Visual C# proje düğümü altında myprojectnode ile yeni Project iletişim kutusundaki Project types klasör ağacının ekran görüntüsü.](../../extensibility/internals/media/myprojectnode.png)

    **myprojectnode** , Visual C# ' nin yalnızca Windows düğümünün altında bir alt düğümü olarak görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni Proje Oluşturma: Arka Plan, 2. Bölüm](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
