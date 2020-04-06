---
title: 'Yeni Proje Üretimi: Hood altında, Part One | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aca35e85e57a07a2b411a23d81b99cff9983b9c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707062"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Yeni Proje Oluşturma: Altyapı Öğeleri, Bölüm Bir
Kendi proje tipinizi nasıl oluşturabilirsiniz hiç düşündünmü? Yeni bir proje oluşturduğunuzda gerçekte ne olur acaba? Kaputun altına bir göz atalım ve gerçekte neler olduğuna bakalım.

 Visual Studio'nun sizin için koordine ettiği birkaç görev vardır:

- Kullanılabilir tüm proje türlerinden bir ağaç görüntüler.

- Her proje türü için uygulama şablonlarının listesini görüntüler ve birini seçmenizine olanak tanır.

- Proje adı ve yol gibi uygulama için proje bilgilerini toplar.

- Bu bilgileri proje fabrikasına aktarın.

- Geçerli çözümde proje öğeleri ve klasörleri oluşturur.

## <a name="the-new-project-dialog-box"></a>Yeni Proje İletişim Kutusu
 Her şey, yeni bir proje için proje türü seçtiğinizde başlar. **Dosya** menüsünde Yeni **Proje'yi** tıklayarak başlayalım. **Yeni Proje** iletişim kutusu şuna benzer bir şekilde görüntülenir:

 ![Yeni Proje iletişim kutusu](../../extensibility/internals/media/newproject.gif "Yeni Proje")

 Şimdi bunlara daha yakından bakalım. **Proje türleri** ağaç oluşturabileceğiniz çeşitli proje türlerini listeler. **Visual C# Windows**gibi bir proje türü seçtiğinizde, başlangıç için uygulama şablonlarının bir listesini görürsünüz. **Visual Studio yüklü şablonlar** Visual Studio tarafından yüklenir ve bilgisayarınızın herhangi bir kullanıcısı tarafından kullanılabilir. Oluşturduğunuz veya topladığınız yeni şablonlar **Şablonlarım'a** eklenebilir ve yalnızca sizin için kullanılabilir.

 **Windows Uygulaması**gibi bir şablon seçtiğinizde, iletişim kutusunda uygulama türünün açıklaması görüntülenir; Bu durumda, **Windows kullanıcı arabirimi ile bir uygulama oluşturmak için bir proje.**

 **Yeni Proje** iletişim kutusunun alt kısmında, daha fazla bilgi toplayan birkaç denetim görürsünüz. Gördüğünüz denetimler proje türüne bağlıdır, ancak genellikle proje **Adı** metin kutusu, **Konum** metin kutusu ve ilgili **Gözat** düğmesi ve **Çözüm Adı** metin kutusu ve çözüm için ilgili **Oluştur dizini** içerir.

## <a name="populating-the-new-project-dialog-box"></a>Yeni Proje İletişim Kutusu'nu Doldurma
 **Yeni Proje** iletişim kutusu bilgilerini nereden alır? Burada iki mekanizma iş başında, biri küçümsenmiş. **Yeni Proje** iletişim kutusu, her iki mekanizmadan elde edilen bilgileri birleştirir ve görüntüler.

 Eski (amortismana alınmış) yöntem, sistem kayıt defteri girişlerini ve .vsdir dosyalarını kullanır. Bu mekanizma Visual Studio açıldığında çalışır. Yeni yöntem .vstemplate dosyalarını kullanır. Bu mekanizma Visual Studio'nun başlatılmasında çalışır, örneğin,

```
devenv /setup
```

 or

```
devenv /installvstemplates
```

### <a name="project-types"></a>Proje Türleri
 **Visual C#** ve **Diğer Diller**gibi **Proje türlerinin** kök düğümlerinin konumu ve adları sistem kayıt defteri girişleri tarafından belirlenir. **Veritabanı** ve **Akıllı Aygıt**gibi alt düğümlerin organizasyonu, karşılık gelen .vstemplate dosyalarını içeren klasörlerin hiyerarşisini yansıtmaktadır. Önce kök düğümlerine bakalım.

#### <a name="project-type-root-nodes"></a>Proje Türü Kök Düğümleri
 İlkolarak başharfe çevrilirken, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje **türü** ağacının kök düğümlerini oluşturmak ve adlandırmak için sistem kayıt defteri anahtarı HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs alt tuşlarına geçer. Bu bilgiler daha sonra kullanılmak üzere önbelleğe alındırılır. TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}\\/1 tuşu ile bakın. Her giriş bir VSPackage GUID'dir. Alt anahtar (/1) adı yoksayılır, ancak varlığı bu bir **Proje türleri** kök düğümü olduğunu gösterir. Bir kök düğümü, **Sırayla Proje türleri** ağacında görünümünü denetleyen birkaç alt anahtara sahip olabilir. Bazılarına bakalım.

##### <a name="default"></a>(Varsayılan)
 Bu, kök düğümünü alan yerelleştirilmiş dizekaynak kimliğidir. String kaynağı, VSPackage GUID tarafından seçilen uydu DLL'de bulunur.

 Örnekte, VSPackage GUID

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 ve kök düğümün kaynak kimliği (varsayılan değer) (/1) #2345

 Yakındaki Paketler tuşundaki GUID'e bakıp SatelliteDll alt anahtarını incelerseniz, dize kaynağını içeren derleme yolunu bulabilirsiniz:

 \<Visual Studio kurulum yolu>\VC#\VCSPackages\1033\csprojui.dll

 Bunu doğrulamak için Dosya Gezgini'ni açın ve csprojui.dll'yi Visual Studio dizinine sürükleyin... String tablosu kaynak #2345 visual **C#** başlığına sahip olduğunu gösterir.

##### <a name="sortpriority"></a>SıralamaÖnceliği
 Bu, **Proje türleri** ağacındaki kök düğümünün konumunu belirler.

 SıralamaÖnceliği REG_DWORD 0x00000014 (20)

 Öncelik sayısı ne kadar düşükse, ağaçtaki konum da o kadar yüksek olur.

##### <a name="developeractivity"></a>Geliştirici Etkinliği
 Bu alt anahtar varsa, kök düğümün konumu Geliştirici Ayarları iletişim kutusu tarafından denetlenir. Örneğin,

 DeveloperActivity REG_SZ VC #

 Visual Studio geliştirme için [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ayarlanmışsa Visual C# kök düğümü olacağını gösterir. Aksi takdirde, **Diğer Dillerin**bir alt düğüm olacaktır.

##### <a name="folder"></a>Klasör
 Bu alt anahtar varsa, kök düğüm belirtilen klasörün alt düğümü olur. Olası klasörlerin listesi anahtarın altında görünür

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 Örneğin, Veritabanı Projeleri girişinde, PseudoFolders'daki Diğer Proje Türleri girişiyle eşleşen bir Klasör anahtarı vardır. Yani, **Proje türleri** ağacında, **Veritabanı Projeleri** Diğer **Proje Türlerinin**alt düğümü olacaktır.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Proje Türü Alt Düğümler ve .vstdir Dosyaları
 **Proje türleri** ağacındaki alt düğümlerin konumu, ProjectTemplates klasörlerinde bulunan klasörlerin hiyerarşisini izler. Makine şablonları için **(Visual Studio yüklü şablonlar),** tipik konum \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ ve kullanıcı şablonları için **(Şablonlarım),** tipik konum \Belgelerim\Visual Studio 14.0\Templates\ProjectTemplates\\' dir. Bu iki konumdan klasör hiyerarşileri Proje **türleri** ağacı oluşturmak için birleştirilir.

 C# geliştirici ayarlarına sahip Visual Studio için **Proje türleri** ağacı aşağıdaki gibi görünür:

 ![Proje Türleri](../../extensibility/internals/media/projecttypes.png "Proje Türleri")

 İlgili ProjectTemplates klasörü aşağıdaki gibi görünür:

 ![Proje Şablonları](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")

 Yeni **Proje** iletişim kutusu açıldığında, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ProjectTemplates klasöründe gezinir ve proje **türleri** ağacındaki yapısını bazı değişikliklerle yeniden oluşturur:

- **Proje türleri** ağacındaki kök düğüm, uygulama şablonu tarafından belirlenir.

- Düğüm adı yerelleştirilmiş olabilir ve özel karakterler içerebilir.

- Sıralama sırası değiştirilebilir.

##### <a name="finding-the-root-node-for-a-project-type"></a>Proje Türü için Kök Düğümünü Bulma
 Visual Studio ProjectTemplates klasörlerini geçtiğinde, tüm .zip dosyalarını açar ve .vstemplate dosyalarını ayıklar. .vstemplate dosyası, bir uygulama şablonu tanımlamak için XML kullanır. Daha fazla bilgi için [Bkz. Yeni Proje Oluşturma: Hood altında, Bölüm İki](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 \<ProjectType> etiketi, uygulama için proje türünü belirler. Örneğin, \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip dosyası bu etiketi içeren bir EmptyProject.vstemplate dosyası içerir:

```
<ProjectType>CSharp</ProjectType>
```

 ProjectTypes> etiketi, ProjectTemplates klasöründeki alt klasör değil, Proje türleri ağacında bir uygulamanın kök düğümünü belirler. **Project types** \< Örnekte, Windows CE uygulamaları Visual **C#** kök düğümüaltında görünür ve WindowsCE klasörünü VisualBasic klasörüne taşısanız bile, Windows CE uygulamaları yine de **Visual C#** kök düğümünün altında görünür.

##### <a name="localizing-the-node-name"></a>Düğüm Adını Yerelleştirme
 Visual Studio ProjectTemplates klasörlerinde geçtiğinde, bulduğu .vstdir dosyalarını inceler. .vstdir dosyası, **Yeni Proje** iletişim kutusunda proje türünün görünümünü kontrol eden bir XML dosyasıdır. .vstdir dosyasında, Proje \< **türleri** düğümadını almak için LocalizedName> etiketini kullanın.

 Örneğin, \CSharp\Database\TemplateIndex.vstdir dosyası şu etiketi içerir:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Bu, bu durumda, **Veritabanı**kök düğümünü adlandıran yerelleştirilmiş dizeuydu DLL ve kaynak kimliğini belirler. Yerelleştirilmiş ad, **.NET**gibi klasör adları için kullanılamayan özel karakterler içerebilir.

 LocalizedName> etiketi yoksa, \<proje türü klasörün kendisi tarafından adlandırılır, **SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Proje Türü için Sıralama Sırasını Bulma
 Proje türünün sıralama sırasını belirlemek için ,vstdir dosyaları SortOrder> etiketini \<kullanır.

 Örneğin, \CSharp\Windows\Windows.vstdir dosyası şu etiketi içerir:

```
<SortOrder>5</SortOrder>
```

 \CSharp\Database\TemplateIndex.vstdir dosyasının daha büyük değeri olan bir etiketi vardır:

```
<SortOrder>5000</SortOrder>
```

 SortOrder> etiketindeki sayı ne kadar düşükse, ağaçtaki konum da o kadar yüksek olur, böylece **Windows** düğümü **Proje türleri** ağacındaki Veritabanı düğümünden daha yüksek görünür. **Database** \<

 Proje \<türü için SortOrder> etiketi belirtilmemişse, Sıralama Siparişi> \<belirtimleri içeren proje türlerini izleyen alfabetik sırada görünür.

 Belgelerim **(Şablonlarım)** klasörlerinde .vstdir dosyası bulunmadığını unutmayın. Kullanıcı uygulaması proje türü adları yerelleştirilmez ve alfabetik sırada görünür.

#### <a name="a-quick-review"></a>Hızlı İnceleme
 **Yeni Proje** iletişim kutusunu değiştirelim ve yeni bir kullanıcı projesi şablonu oluşturalım.

1. \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp klasörüne MyProjectNode alt klasörü ekleyin.

2. Herhangi bir metin düzenleyicisini kullanarak MyProjectNode klasöründe bir MyProject.vstdir dosyası oluşturun.

3. .vstdir dosyasına şu satırları ekleyin:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. .vstdir dosyasını kaydedin ve kapatın.

5. Herhangi bir metin düzenleyicisini kullanarak MyProjectNode klasöründe bir MyProject.vstemplate dosyası oluşturun.

6. Bu satırları .vstemplate dosyasına ekleyin:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. The.vstemplate dosyasını kaydedin ve düzenleyiciyi kapatın.

8. .vstemplate dosyasını yeni sıkıştırılmış MyProjectNode\MyProject.zip klasörüne gönderin.

9. Visual Studio komut penceresinden şunları yazın:

    ```
    devenv /installvstemplates
    ```

   Visual Studio'yu açın.

10. Yeni **Proje** iletişim kutusunu açın ve Visual C# proje düğümündeki genişledin. **Visual C#**

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode,** Windows düğümünün hemen altında Visual C# alt düğümü olarak görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni Proje Oluşturma: Altyapı Öğeleri, Bölüm İki](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
