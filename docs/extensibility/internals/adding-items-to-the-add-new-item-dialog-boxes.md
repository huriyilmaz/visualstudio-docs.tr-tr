---
title: Yeni Öğe Ekle İletişim Kutularına Öğe Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7f9e5c792785a23ad1674a50abeb4eb6d3cba9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710211"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekle iletişim kutusuna öğe ekleme
**Yeni Öğe Ekle** iletişim kutusuna öğe ekleme işlemi kayıt defteri anahtarlarıyla başlar. Aşağıdaki kayıt defteri girişlerinde gösterildiği gibi, **AddItemTemplates** bölümü, **Yeni Öğe Ekle** iletişim kutusunda kullanıma sunulan öğelerin konulduğu dizinin yolunu ve adını içerir.

> [!NOTE]
> Kod kesimini hemen izleyen tablo, kayıt defteri girişi hakkında ek bilgiler içerir.

 Bu bölüm **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**altında yer almaktadır.

 İlk GUID bu tür projeler için CLSID olduğunu; ikinci GUID, Öğeleri Ekle şablonları için kayıtlı proje türünü gösterir:

 **\\{C061DB26-5833-11D2-96F5-000000000000} \\AddItemTemplates\\TemplatesDir\\{ACEF4EB2-57CF-11D2-96F4-0000000000}\\1**

 **@**= #6

 **ŞablonlarDir** = \\&lt;Visual Studio SDK\\&lt;kurulum&gt;\\&lt;yolu&gt;\\&gt;\\&lt;VSIntegration&gt;\\&lt;SomeFolder SomePackage SomeProject SomeProjectItems&gt;

 **SıralamaÖnceliği** = dword:00000064

| Adı | Tür | Veriler *(.rgs* dosyasından) | Açıklama |
|------------------|-----------| - | - |
| @ (Varsayılan) | REG_SZ | #%IDS_ADDITEM_TEMPLATES_ENTRY% | **Madde Ekle** şablonları için kaynak kimliği. |
| Val ŞablonlarıDir | REG_SZ | %TEMPLATE_PATH\\&lt;Bazı Proje Öğeleri&gt; | **Yeni Öğe Ekle** sihirbazı için iletişim kutusunda görüntülenen proje öğelerinin yolu. |
| Val SıralamaÖnceliği | REG_DWORD | 100[!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]( ) | **Yeni Öğe Ekle** iletişim kutusunda görüntülenen dosyaların ağaç düğümündeki sıralama sırasını belirler. |

> [!NOTE]
> Visual C# ve Visual Basic proje türleri için GUIDS aşağıdaki gibidir:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 %TEMPLATE_PATH *SomeProjectItems\\&lt;&gt;* olan **TemplatesDir**için listelenen dizin, **Yeni Öğe Ekle** iletişim kutusu ağacının sol tarafındaki düğümdür. Ağaçtaki ek öğeler, bu kök dizininiçindeki alt dizini temel adamaktadır. Projeye eklenecek dosyalar, **Yeni Öğe Ekle** iletişim kutusunun sağ bölmesindeki öğelerdir.

 Genellikle, bu klasör, şablon HTML veya *.cpp* dosyası gibi projeniz için şablon dosyaları ve sihirbazları başlatmak için herhangi bir *.vsz* dosyaları içerir. Öğelerin nasıl görüntüleneceğini denetlemek için dizin adlarını ve simgelerini yerelleştirmek için *.vsdir* dosyalarını da ekleyebilirsiniz. Yerelleştirilmiş dize, **Yeni Öğe Ekle** iletişim kutusundaki bu düğümü temsil eden iletişim kutusunda görünen başlıktır.

 Ancak, her şeyi tek bir *.vsdir* dosyasında olması gerekmez. Dizindeki her öğe için bir *.vsdir* dosyası nız olabilir. Daha fazla bilgi için [Sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md) ve [Şablon dizin açıklaması (.vsdir) dosyalarına](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)bakın.

> [!NOTE]
> Şablon dizinlerinde *.vsdir* dosyaları isteğe bağlıdır. Yalnızca dizine bir proje öğesi koymak ve **Yeni Öğe Ekle** iletişim kutusunda görüntülemek istiyorsanız, bu dosyayı **TemplatesDir** deyiminde belirtilen şablondizine koyabilirsiniz. Dosya daha sonra bu proje için **Yeni Öğe Ekle** iletişim kutusunun sağ bölmesinde görüntülenir. Ancak, dosya veya simge için yerelleştirilmiş bir resim yazısı görüntülemek istiyorsanız, şablondizine en az bir *.vsdir* dosyası eklemeniz gerekir.

## <a name="group-project-items"></a>Proje öğelerini gruplandırma
 **Yeni Öğe Ekle** iletişim kutusu ağacındaki klasörlerde şablon grupları eklemek istiyorsanız, kök şablon dizininin altında öğelerin bulunduğu alt dizinler olmalıdır. Yeni **Öğe Ekle** iletişim kutusu kullanıcılara görüntülendiğinde, alt klasörleri de görür ve onlardan proje öğelerini seçebilirler.

 Kod kesimindeki sıralama önceliği, bu şablon dizininin ağaç düğümünün diğer öğelerine göre ağaçta nerede oluşturulacağını belirler. Yeni **Öğe Ekle** iletişim kutusu için, öğelerinizin iletişim kutusunda doğru konumda görüntülenmesi için ekleme önceliği, eklemeniz gereken tek şeydir.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> **Arabirimi, Yeni Öğe Ekle** iletişim kutusunda görüntülenenlere filtre uygulamak için de uygulayabilirsiniz. Bu arabirimi uygulayarak, diskte örneğin 50 şablon ve sihirbaz dosyası içeren bir şablon dizini ayarlayabilirsiniz. Bu şekilde, bir proje türüne ait 20 dosya, başka bir proje türüne ait diğer 30 dosya ve genel bir proje türünde kullanılabilen tüm dosyalarla farklı proje türleri olabilir. Bu şekilde, hangi proje şablonunun oluşturulduğuna bağlı olarak, farklı bir şablon dosyası kümesi görüntüleyebilirsiniz.

 Örneğin, Visual Basic projesinde Web projeleri ve istemci projeleriniz olabilir. Web formları istemci projesine eklemek için yararlı öğeler değildir ve windows formları bir Web sunucusu projesine eklemek için yararlı öğeler değildir. Bu nedenle, her iki proje türü için tüm dosyaları içeren bir şablon dizini oluşturabilirsiniz. Daha <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>sonra, uygulayarak, projedeki proje veya proje ayarlarının türüne göre görüntülenmemesi gereken öğeleri gizleyebilirsiniz.

## <a name="filter-project-items"></a>Proje öğelerini filtreleme
 `IVsFilterAddProjectItemDlg2`ağaç (sol bölme) ve proje dosyaları (sağ bölme) öğeleri aşağıdaki yollarla filtreleme sağlar:

- Yerelleştirilmiş adlar *(.vsdir* dosyasında bulunan iletişim kutusunda görüntülenen altyazılar) `IVsFilterAddProjectItemDlg`tarafından sağlanan .

- Diskteki dosya ve klasörlerin gerçek adlarına göre (yerelleştirilmeyen — no `IVsFilterAddProjectItemDlg` *.vsdir* dosyası) tarafından sağlanan .

- Kategoriye göre, `IVsFilterAddProjectItemDlg2`tarafından sağlanan .

  Kategoriye göre filtre uygulayacak şekilde, Visual Basic'teki Web *formu* veya *İstemci öğesi* gibi *.vsdir* dosyasındaki bir öğeye kategori dizesi sağlayın. İletişim kutusu kodu daha sonra *.vsdir* dosyasından kategori sınıflandırmasını alır ve size iletir. Daha sonra, **Yeni Öğe** Ekle `IVsFilterAddProjectItemDlg2` iletişim kutusunu kategorilere göre filtrelemek için bu bilgileri uygulamanıza aktarabilirsiniz. Öğeleri Web sayfaları için veya istemci Win32 uygulama örnekleri olarak da filtreleyebilirsiniz. Ayrıca, etiketli öğeleri [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Microsoft Hazırlık Sınıfları (MFC) veya etkin şablon kitaplığı (ATL) öğeleri olarak tanımlayabilirsiniz. Bu öğeleri tanımladığınızda, proje sistemi kendi sınıflandırmalarını tanımlayabilir, böylece sistem kategorilere ve sınıflandırmalara göre filtrelenebilir.

  Bu filtre işlevini uygularsanız, gizli olması gereken her öğenin bir tablosunu eşlemeniz gerekmez. Öğeleri yalnızca türlere sınıflandırabilir ve sınıflandırmaları *.vsdir* dosyasına veya dosyalarına koyabilirsiniz. Ardından, arabirimi uygulayarak belirli bir sınıflandırmaya sahip öğelerden herhangi birini gizleyebilirsiniz. Bu şekilde, **Yeni Öğe Ekle** iletişim kutusundaki öğeleri projedeki duruma göre dinamik hale getirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Proje ve madde şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [Genellikle projeleri genişletmek için kullanılan nesnelerin CATID'leri](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Şablon dizin açıklaması (.vsdir) dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
