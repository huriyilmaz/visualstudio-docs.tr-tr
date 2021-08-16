---
title: Yeni Öğe Ekle İletişim Kutularına Öğe Ekleme | Microsoft Docs
description: Projelerde kullanmak üzere şablonları ve proje öğelerini görüntüley Visual Studio yeni öğe ekle iletişim kutusuna öğe ekleme hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9250ee676b823f470f87d8f339b7a19d5ceca7232cda7dda0ec49cd8b5ec89b1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448304"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekle iletişim kutusuna öğe ekleme
Yeni Öğe Ekle iletişim kutusuna **öğe ekleme** işlemi kayıt defteri anahtarları ile başlar. Aşağıdaki kayıt defteri girdilerinde gösterildiği gibi **AddItemTemplates** bölümü, Yeni Öğe Ekle iletişim kutusunda  kullanılabilir yapılan öğelerin yer alan dizininin yolunu ve adını içerir.

> [!NOTE]
> Kod kesiminin hemen takip eden tablosu, kayıt defteri girişi hakkında ek bilgiler içerir.

 Bu bölüm, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects.**

 İlk GUID, bu tür projeler için CLSID'tir; İkinci GUID, Öğe Ekle şablonları için kayıtlı proje türünü gösterir:

 **\\{C061DB26-5833-11D2-96F5-000000000000} \\ AddItemTemplates \\ TemplatesDir \\ {ACEF4EB2-57CF-11D2-96F4-00000000000} \\ 1**

 **@** = #6

 **TemplatesDir**  =  \\ &lt; Visual Studio SDK yükleme yolu &gt; \\ VSIntegration \\ &lt; SomeFolder &gt; \\ &lt; SomePackage &gt; \\ &lt; SomeProject &gt; \\ &lt; SomeProjectItems&gt;

 **SortPriority** = dword:00000064

| Ad | Tür | Veriler *(.rgs dosyasından)* | Açıklama |
|------------------|-----------| - | - |
| @ (Varsayılan) | REG_SZ | #%IDS_ADDITEM_TEMPLATES_ENTRY% | Öğe Ekle **şablonları için** Kaynak Kimliği. |
| Val TemplatesDir | REG_SZ | %TEMPLATE_PATH% \\ &lt; SomeProjectItems&gt; | Yeni Öğe Ekle sihirbazının iletişim kutusunda görüntülenen **proje öğelerinin** yolu. |
| Val SortPriority | REG_DWORD | 100 ( [!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)] ) | Yeni Öğe Ekle iletişim kutusunda görüntülenen dosyaların ağaç düğümünde **sıralama sıralamayı** belirler. |

> [!NOTE]
> Visual C# ve Visual Basic proje türleri için GUID'ler aşağıdaki gibidir:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 **TemplatesDir** için listelenen ve *\\ &lt; %TEMPLATE_PATH% SomeProjectItems &gt;* olan dizin, Yeni Öğe Ekle iletişim kutusu ağacının **sol** tarafındaki düğüm. Ağaçtaki ek öğeler, bu kök dizin içindeki alt dizini temel alan öğelerdir. Projeye eklenecek dosyalar, Yeni Öğe Ekle iletişim kutusunun sağ **bölmesindeki öğelerdir.**

 Bu klasör genellikle projeniz için şablon HTML veya *.cpp* dosyası gibi şablon dosyalarını ve sihirbazları başlatmaya yönelik *.vsz* dosyalarını içerir. Öğelerin nasıl görüntüleniyor olduğunu kontrol etmek için dizin adlarını ve simgelerini *yerelleştirmeye uygun .vsdir* dosyalarını da dahilebilirsiniz. Yerelleştirilmiş dize, yeni öğe ekle iletişim kutusu ağacında bu düğümü temsil eden iletişim kutusunda **görünen açıklamalı alt** yazıdır.

 Ancak, her şeyi tek bir *.vsdir dosyasında bulundurabilirsiniz.* Dizinde her öğe *için bir .vsdir* dosyanız olabilir. Daha fazla bilgi için [bkz. Sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md) ve [Şablon dizini açıklaması (.vsdir) dosyaları.](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

> [!NOTE]
> Şablon *dizinlerinde .vsdir* dosyaları isteğe bağlıdır. Yalnızca dizine bir proje öğesi eklemek ve bunu  Yeni Öğe Ekle iletişim kutusunda görüntülemek için, bu dosyayı **TemplatesDir** deyiminde belirtilen şablonlar dizinine koyabilirsiniz. Dosya daha sonra bu proje için Yeni Öğe Ekle **iletişim kutusunun sağ** bölmesinde görüntülenir. Ancak, dosya veya simge için yerelleştirilmiş bir açıklamalı alt yazı görüntülemek için templates dizinine en az bir *.vsdir* dosyası dahil etmek gerekir.

## <a name="group-project-items"></a>Proje öğelerini grupla
 Şablon gruplarını Yeni Öğe Ekle iletişim  kutusu ağacının klasörlerde yer almak için kök şablon dizininin altında öğeleri içeren alt dizinler olmalıdır. Kullanıcılara **Yeni Öğe** Ekle iletişim kutusu görüntülendiğinde, alt klasörleri de görebilir ve bunlardan proje öğelerini seçeler.

 Kod segmentinde sıralama önceliği, ağaç düğümünün diğer öğelerine göre ağaçta bu şablon dizininin oluşturulacak yeri belirler. Yeni **Öğe Ekle** iletişim kutusu için sıralama önceliği, öğelerinizin iletişim kutusunda doğru konumda görüntülenebilir olması için dahil etmek istediğiniz önceliktir.

 Yeni Öğe Ekle <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> iletişim kutusunda görüntülenenleri filtrelemek için **arabirimini de** kullanabilirsiniz. Bu arabirimi kullanarak diskte 50 şablon ve sihirbaz dosyası içeren bir şablon dizini oluşturabilirsiniz. Bu şekilde, bir proje türüne ait 20 dosya, başka bir proje türüne ait olan diğer 30 dosya ve genel bir proje türünde kullanılabilen tüm dosyalar ile farklı proje türlerine sahip olabilirsiniz. Bu şekilde, oluşturulan proje şablonuna bağlı olarak farklı bir şablon dosyası kümesi görüntüebilirsiniz.

 Örneğin, bir Visual Basic projesinde Web projeleriniz ve istemci projeleriniz olabilir. Web formları bir istemci projesine eklemek için kullanışlı öğeler değildir ve Windows formları bir Web sunucusu projesine eklemek için kullanışlı öğeler değildir. Bu nedenle, her iki proje türü için tüm dosyaları içeren bir şablon dizini oluşturabilirsiniz. Ardından, uygulayarak, projedeki proje türüne veya proje ayarlarına göre <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> görüntülenmez öğeleri gizleyebilirsiniz.

## <a name="filter-project-items"></a>Proje öğelerini filtreleme
 `IVsFilterAddProjectItemDlg2` , ağaç (sol bölme) ve proje dosyalarında (sağ bölme) aşağıdaki yollarla öğelerin filtresini sağlar:

- tarafından sağlanan yerelleştirilmiş adlarla *(.vsdir* dosyasında yer alan iletişim kutusunda görüntülenen açıklamalı alt `IVsFilterAddProjectItemDlg` yazılar).

- tarafından sağlanan disk (yerelleştirilmiş olmayan — *.vsdir* dosyası yok) dosya ve klasörlerin gerçek adlarına `IVsFilterAddProjectItemDlg` göre.

- tarafından sağlanan kategoriye `IVsFilterAddProjectItemDlg2` göre.

  Kategoriye göre filtrelemek için *, .vsdir* dosyasındaki web  formu veya İstemci öğesi gibi bir öğeye bir kategori *dizesi* Visual Basic. İletişim kutusu kodu daha sonra kategori sınıflandırmasını *.vsdir* dosyasından alıyor ve size iletir. Ardından, Yeni Öğe Ekle iletişim kutusunu kategorilere `IVsFilterAddProjectItemDlg2` göre filtrelemek için **bu bilgileri uygulamanıza** geçebilirsiniz. Öğeleri Web sayfaları için veya istemci Win32 uygulama örnekleri olarak da filtreleyebilirsiniz. Ayrıca, etiketlenmiş öğeleri Microsoft Foundation Sınıfları (MFC) veya etkin şablon kitaplığı [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] (ATL) öğeleri olarak tanımlayabilirsiniz. Bu öğeleri tanımladığınız zaman, sistemin kategorilere ve sınıflandırmalara göre filtrelenmiş olması için proje sistemi kendi sınıflandırmalarını tanımlayabilir.

  Bu filtre işlevini uygulamaya alırsanız, gizlenen her öğenin bir tabloyu eşlemeniz gerekli değildir. Öğeleri türler olarak sınıflandırarak sınıflandırmaları *.vsdir* dosyasına veya dosyalarına koyabilirsiniz. Ardından arabirimini kullanarak belirli bir sınıflandırmaya sahip öğelerden herhangi birini gizleyebilirsiniz. Bu şekilde, Yeni Öğe Ekle iletişim kutusundaki **öğeleri** projedeki durumu temel alarak dinamik hale ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [Projeleri genişletmek için genellikle kullanılan nesneler için CATID'ler](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Şablon dizini açıklaması (.vsdir) dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
