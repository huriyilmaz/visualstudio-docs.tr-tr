---
title: 'Yeni proje oluşturma: devlet, birinci bölüm | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41b2b229fe343c9f6d515ba757e4bd976ee7fda5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726523"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Yeni Proje Oluşturma: Altyapı Öğeleri, Bölüm Bir
Kendi proje türünü nasıl oluşturacağınız hakkında düşündük? Yeni bir proje oluşturduğunuzda gerçekten ne olduğunu merak ediyor musunuz? Ayrıca, aşın altında bir göz atalım ve nelerin gerçekten devam ettiğinin yanı sıra.

 Visual Studio 'Nun sizin için eşgüdümünü sağlayan birkaç görev vardır:

- Tüm kullanılabilir proje türlerinin bir ağacını görüntüler.

- Her proje türü için uygulama şablonlarının bir listesini görüntüler ve bir tane seçmenizi sağlar.

- Uygulama için proje adı ve yol gibi proje bilgilerini toplar.

- Bu bilgileri proje fabrikasına geçirir.

- Geçerli çözümde proje öğeleri ve klasörleri oluşturur.

## <a name="the-new-project-dialog-box"></a>Yeni proje Iletişim kutusu
 Yeni proje için bir proje türü seçtiğinizde, hepsi başlar. **Dosya** menüsünde **Yeni proje ' ye** tıklayarak başlayalım. **Yeni proje** iletişim kutusu görünür ve aşağıdakine benzer şekilde görünür:

 ![Yeni proje iletişim kutusu](../../extensibility/internals/media/newproject.gif "NewProject")

 Daha yakından göz atalım. **Proje türleri** ağacı, oluşturabileceğiniz çeşitli proje türlerini listeler. **Visual C# Windows**gibi bir proje türü seçtiğinizde, başlamanızı sağlamak için uygulama şablonlarının bir listesini görürsünüz. Visual **Studio yüklü şablonlar** , Visual Studio tarafından yüklenir ve bilgisayarınızın tüm kullanıcıları tarafından kullanılabilir. Oluşturduğunuz veya topladığınız yeni şablonlar **Şablonlarıma** eklenebilir ve yalnızca sizin için kullanılabilir.

 **Windows uygulaması**gibi bir şablon seçtiğinizde, iletişim kutusunda uygulama türünün bir açıklaması görüntülenir; Bu durumda, bir **Windows Kullanıcı arabirimiyle uygulama oluşturmaya yönelik bir proje**.

 **Yeni proje** iletişim kutusunun en altında, daha fazla bilgi toplayan birkaç denetim görürsünüz. Gördüğünüz denetimler proje türüne bağlıdır, ancak genellikle bir proje **adı** metin kutusu, bir **konum** metin kutusu ve ilgili **gezinme** düğmesi ve çözüm için bir **çözüm adı** metin kutusu ve ilgili **oluşturma dizini içerirler.** onay kutusu.

## <a name="populating-the-new-project-dialog-box"></a>Yeni proje Iletişim kutusunu doldurma
 **Yeni proje** iletişim kutusu nereden bilgilerini alır? Burada çalışan iki mekanizma vardır, bunlardan biri kullanımdan kaldırılmıştır. **Yeni proje** iletişim kutusu her iki mekanizmalardan elde edilen bilgileri birleştirir ve görüntüler.

 Eski (kullanım dışı) yöntemi sistem kayıt defteri girişlerini ve. vsdir dosyalarını kullanır. Bu mekanizma, Visual Studio açıldığında çalışır. Yeni yöntem. vstemplate dosyalarını kullanır. Bu mekanizma, Visual Studio başlatıldığında çalışır, örneğin

```
devenv /setup
```

 veya

```
devenv /installvstemplates
```

### <a name="project-types"></a>Proje Türleri
 **Görsel C#**  ve **diğer diller**gibi **Proje türleri** kök düğümlerinin konumu ve adları sistem kayıt defteri girdilerine göre belirlenir. **Veritabanı** ve **akıllı cihaz**gibi alt düğümlerin organizasyonu, karşılık gelen. vstemplate dosyalarını içeren klasörlerin hiyerarşisini yansıtır. Önce kök düğümlere göz atalım.

#### <a name="project-type-root-nodes"></a>Proje türü kök düğümleri
 @No__t_0 başlatıldığında, **Proje türleri** ağacının kök düğümlerini derlemek ve adlandırmak için HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs sistem kayıt defteri anahtarının alt anahtarlarından geçer. Bu bilgiler daha sonra kullanılmak üzere önbelleğe alınır. TemplateDirs \\ {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\/1 anahtarına bakın. Her giriş bir VSPackage GUID 'sidir. Alt anahtarın adı (/1) yoksayıldı, ancak varlığı bunun bir **Proje türü** kök düğümü olduğunu gösterir. Kök düğüm, **Proje türleri** ağacındaki görünümünü denetleyen birkaç alt anahtarda bulunabilir. Şimdi bunlara göz atalım.

##### <a name="default"></a>(Varsayılan)
 Bu, kök düğümü isimeden yerelleştirilmiş dizenin kaynak KIMLIĞIDIR. Dize kaynağı, VSPackage GUID tarafından seçilen uydu DLL 'sinde bulunur.

 Örnekte, VSPackage GUID 'SI

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 ve kök düğümün (/1) kaynak KIMLIĞI (varsayılan değer) #2345

 Yakındaki paketler anahtarındaki GUID 'YI arar ve SatelliteDll alt anahtarını incelerseniz, dize kaynağını içeren derlemenin yolunu bulabilirsiniz:

 \<Visual Studio yükleme yolu > \VC#\Vcspackages\10\csprojuı.dll

 Bunu doğrulamak için dosya gezginini açın ve csprojuı. dll dosyasını Visual Studio dizinine sürükleyin. Dize tablosu, kaynak #2345 başlık **görselinin C#** olduğunu gösterir.

##### <a name="sortpriority"></a>SortPriority
 Bu, kök düğümün **Proje türleri** ağacındaki konumunu belirler.

 SortPriority REG_DWORD 0x00000014 (20)

 Önceliğin sayısı düşükse, ağaçtaki konum daha yüksektir.

##### <a name="developeractivity"></a>DeveloperActivity
 Bu alt anahtar varsa, kök düğümün konumu Geliştirici ayarları iletişim kutusu tarafından denetlenir. Örneğin,

 DeveloperActivity REG_SZVC#

 Visual Studio [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] C# geliştirme için ayarlandıysa, görselin bir kök düğüm olacağını gösterir. Aksi takdirde, **diğer dillerin**alt düğümü olur.

##### <a name="folder"></a>Klasör
 Bu alt anahtar varsa, kök düğüm belirtilen klasörün bir alt düğümü haline gelir. Anahtar altında olası klasörlerin listesi görüntülenir

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 Örneğin, veritabanı projeleri girdisi, sözde klasörlerdeki diğer proje türleri girişiyle eşleşen bir klasör anahtarına sahiptir. Bu nedenle, **Proje türleri** ağacında, **veritabanı projeleri** **diğer proje türlerinin**bir alt düğümü olacaktır.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Proje türü alt düğümleri ve. vstdir dosyaları
 **Proje türleri** ağacındaki alt düğümlerin konumu, ProjectTemplates klasörlerindeki klasörlerin hiyerarşisini izler. Makine şablonları (**Visual Studio yüklü şablonlar**) için, normal konum \Program Files\Microsoft Visual Studio 14.0 \ common7\ıde\projecttemplates\ ve Kullanıcı şablonları (**Şablonlarım**) için, normal konum \Documents \ olur. Visual Studio 14.0 \ Templates\ProjectTemplates \\. Bu iki konumdaki klasör hiyerarşileri, **Proje türleri** ağacı oluşturmak için birleştirilir.

 Visual Studio C# Geliştirici ayarları Için, **Proje türleri** ağacı şuna benzer:

 ![Proje Türleri](../../extensibility/internals/media/projecttypes.png "ProjectTypes")

 Karşılık gelen ProjectTemplates klasörü şöyle görünür:

 ![Proje şablonları](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")

 **Yeni proje** iletişim kutusu açıldığında, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ProjectTemplates klasöründen geçer ve yapı öğesini **Proje türleri** ağacında bazı değişikliklerle yeniden oluşturur:

- **Proje türleri** ağacındaki kök düğüm, uygulama şablonu tarafından belirlenir.

- Düğüm adı yerelleştirilebilecek ve özel karakterler içerebilir.

- Sıralama düzeni değiştirilebilir.

##### <a name="finding-the-root-node-for-a-project-type"></a>Proje türü için kök düğümü bulma
 Visual Studio, ProjectTemplates klasörlerinde gezdiğinde tüm. zip dosyalarını açar ve tüm. vstemplate dosyalarını ayıklar. Bir. vstemplate dosyası bir uygulama şablonunu anlatmak için XML kullanır. Daha fazla bilgi için bkz. [Yeni proje oluşturma: Ikinci bölüm altında](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 @No__t_0ProjectType > etiketi, uygulamanın proje türünü belirler. Örneğin, \Csharp\smartdev>windowsce\10\ce-emptyproject.exe dosyası, bu etikete sahip bir EmptyProject. vstemplate dosyası içeriyor:

```
<ProjectType>CSharp</ProjectType>
```

 @No__t_0ProjectType > etiketi, ancak ProjectTemplates klasöründeki alt klasörü değil, **Proje türleri** ağacındaki bir uygulamanın kök düğümünü belirler. Örnekte, Windows CE uygulamalar **görsel C#**  kök düğümünün altında görünür ve WindowsCE klasörünü VisualBasic klasörüne taşıdıysanız bile, Windows CE uygulamalar hala **görsel C#**  kök altında görünür düğümüne.

##### <a name="localizing-the-node-name"></a>Düğüm adını yerelleştirme
 Visual Studio, ProjectTemplates klasörlerinde gezdiğinde, bulduğu tüm. vstdir dosyalarını inceler. . Vstdir dosyası, **Yeni proje** iletişim kutusundaki Proje türünün görünümünü DENETLEYEN bir XML dosyasıdır. . Vstdir dosyasında, **Proje türleri** düğümünü adlandırmak için \<LocalizedName > etiketini kullanın.

 Örneğin, \Csharp\bir Templateındex.vstdir dosyası şu etiketi içerir:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Bu, kök düğümü, bu durumda **veritabanı**olarak isimleştirilmiş yerelleştirilmiş DIZENIN uydu dll 'sini ve kaynak kimliğini belirler. Yerelleştirilmiş ad, **.net**gibi klasör adları için kullanılamayan özel karakterler içerebilir.

 @No__t_0LocalizedName > etiketi yoksa, proje türü klasör tarafından adlandırılır, **SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Proje türü için sıralama düzenini bulma
 Proje türünün sıralama düzenini öğrenmek için. vstdir dosyaları \<SortOrder > etiketini kullanır.

 Örneğin, \CSharp\Windows\Windows.vstdir dosyası şu etiketi içerir:

```
<SortOrder>5</SortOrder>
```

 \Csharp\bir Templateındex.vstdir dosyasında daha büyük bir değer içeren bir etiket vardır:

```
<SortOrder>5000</SortOrder>
```

 @No__t_0SortOrder > etiketindeki sayı ne kadar düşükse, ağaç içindeki konum daha yüksektir. bu nedenle, **Windows** düğümü **Proje türleri** ağacındaki **veritabanı** düğümünden daha büyük görünür.

 Proje türü için \<SortOrder > etiketi belirtilmemişse, \<SortOrder > belirtimleri içeren proje türlerini izleyen alfabetik sırada görünür.

 Belgelerim (**Şablonlarım**) klasörlerinde. vstdir dosyaları olmadığını unutmayın. Kullanıcı uygulaması proje türü adları yerelleştirilmez ve alfabetik sırada görünür.

#### <a name="a-quick-review"></a>Hızlı bir gözden geçirme
 **Yeni proje** iletişim kutusunu değiştirelim ve yeni bir Kullanıcı projesi şablonu oluşturalım.

1. \Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\CSharp klasörüne bir MyProjectNode alt klasörü ekleyin.

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

8. . Vstemplate dosyasını yeni bir sıkıştırılmış Myprojectnode\myproject.exe klasörüne gönderin.

9. Visual Studio komut penceresinde, şunu yazın:

    ```
    devenv /installvstemplates
    ```

   Visual Studio'yu açın.

10. **Yeni proje** iletişim kutusunu açın ve **görsel C#**  proje düğümünü genişletin.

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode** , yalnızca Windows düğümünün altında bulunan bir C# görsel alt düğüm olarak görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni Proje Oluşturma: Altyapı Öğeleri, Bölüm İki](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)