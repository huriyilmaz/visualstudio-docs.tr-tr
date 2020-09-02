---
title: Yeni öğe Ekle Iletişim kutularına öğe ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecdacfc4ac65e0dc18512bfb56eb870545c66a9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64790714"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Yeni Öğe Ekleme İletişim Kutularına Öğe Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Yeni öğe Ekle** iletişim kutusuna öğe ekleme işlemi kayıt defteri anahtarlarıyla başlar. Aşağıdaki kayıt defteri girişlerinde gösterildiği gibi, AddItemTemplates bölümü, **Yeni öğe Ekle** iletişim kutusunda bulunan öğelerin bulunduğu dizinin yolunu ve adını içerir.  
  
> [!NOTE]
> Kod segmentinden hemen sonraki tablo, kayıt defteri girdisiyle ilgili ek bilgiler içerir.  
  
 Bu bölüm [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects] altında bulunur.  
  
 İlk GUID, bu türdeki projelerin CLSID 'sidir; İkinci GUID, öğe Ekle şablonları için kayıtlı proje türünü gösterir.  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \ 1  
  
 @ = "#6"  
  
 "Templates dir" = " \< Visual STUDIO SDK yükleme yolu \\ \Vsıntelation\somefolder \ \\ \\ somepackage \\ \Someproject \\ \ someprojectıtems"  
  
 "SortPriority" = DWORD: 00000064  
  
|Ad|Tür|Veri (. rgs dosyası)|Description|  
|----------|----------|-----------------------------|-----------------|  
|@ (Varsayılan)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY%|**Öğe şablonları eklemek** IÇIN kaynak kimliği.|  
|Val şablonları dizini|REG_SZ|% TEMPLATE_PATH% \ Someprojectıtems|**Yeni öğe Ekle** sihirbazının iletişim kutusunda görünen proje öğelerinin yolu.|  
|Değer SortPriority|REG_DWORD|100 ( [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)] )|**Yeni öğe Ekle** iletişim kutusunda gösterilecek dosyaların ağaç düğümündeki sıralama düzenini belirler.|  
  
> [!NOTE]
> Visual C# ve Visual Basic proje türleri için GUID 'ler şunlardır: [!INCLUDE[csprcs](../../includes/csprcs-md.md)] : {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] : {F184B08F-C81C-45f6-A57F-5ABD9991F28F}  
  
 % TEMPLATE_PATH% \ Someprojectıtems olan TemplateDirs için listelenen dizin, **Yeni öğe Ekle** iletişim kutusu ağacının sol tarafındaki düğümdür. Ağaçtaki ek öğeler, bu kök dizin içindeki alt dizine dayalıdır. Projeye eklenmek üzere kullanılabilir dosyalar, **Yeni öğe Ekle** iletişim kutusunun sağ bölmesindeki öğelerdir.  
  
 Genellikle, bu klasör, projeniz için bir şablon HTML veya. cpp dosyası ve sihirbazları başlatmak için. vsz dosyaları gibi şablon dosyalarını içerir. Öğelerin nasıl görüntülendiğini denetlemek için dizin adlarını ve simgelerini yerelleştirme için. vsdir dosyalarını da dahil edebilirsiniz. Yerelleştirilmiş dize, yeni öğe Ekle iletişim ağacında bu düğümü temsil eden iletişim kutusunda görünen başlıktır.  
  
 Ancak, tek bir. vsdir dosyasında her şeyin olması gerekmez. Dizindeki her öğe için bir. vsdir dosyanıza sahip olabilirsiniz. Daha fazla bilgi için bkz [. sihirbaz (. Vsz) dosya](../../extensibility/internals/wizard-dot-vsz-file.md) ve [Şablon dizin açıklaması (. Vsdir) dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
> Şablon dizinlerindeki. VSDir dosyaları isteğe bağlıdır. Dizine yalnızca bir proje öğesi eklemek ve bunu **Yeni öğe Ekle** iletişim kutusunda göstermek istiyorsanız, bu dosyayı Templates dır ifadesinde belirtilen Templates dizinine koyabilirsiniz. Bu dosya daha sonra bu proje için **Yeni öğe Ekle** iletişim kutusunun sağ bölmesinde görüntülenecektir. Ancak, dosya veya simge için yerelleştirilmiş bir Başlık göstermek istiyorsanız, şablonlar dizinine en az bir. vsdir dosyası eklemeniz gerekir.  
  
## <a name="grouping-project-items"></a>Proje öğelerini gruplandırma  
 **Yeni öğe Ekle** iletişim kutusu ağacında klasörlerde şablon grupları eklemek istiyorsanız, kök şablon dizini altında bulunan alt dizinlere sahip olmanız gerekir. **Yeni öğe Ekle** iletişim kutusu kullanıcılara görüntülendiğinde, alt klasörleri de görürler ve proje öğelerini buradan seçebileceksiniz.  
  
 Kod kesimindeki sıralama önceliği, ağaç düğümünün diğer öğelerine göre ağaçta bu şablon dizininin nerede oluşturulacağını belirler. **Yeni öğe Ekle** iletişim kutusunda, öğelerin iletişim kutusunda doğru konumda görüntülenebilmesi için sıralama önceliği dahil etmeniz gerekir.  
  
 Ayrıca, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> **Yeni öğe Ekle** iletişim kutusunda neyin görüntülendiğini filtrelemek için arabirimini de uygulayabilirsiniz. Bu arabirimi uygulayarak, örneğin, 50 şablon ve sihirbaz dosyalarını içeren diskte tek bir şablon dizini ayarlayabilirsiniz. Bu şekilde, bir proje türüne ait 20 dosya, başka bir proje türüne ait diğer 30 dosya ve genel bir proje türünde bulunan tüm dosyalar ile farklı proje türlerine sahip olabilirsiniz. Bu şekilde, hangi proje şablonunun oluşturulduğuna bağlı olarak, farklı bir şablon dosyaları kümesi görüntüleyebilirsiniz.  
  
 Örneğin, bir Visual Basic projesinde, Web projelerine ve istemci projelerine sahip olabilirsiniz. Web formları bir istemci projesine eklemek için kullanışlı öğeler değildir ve Windows Forms bir Web sunucusu projesine eklemek için yararlı öğeler değildir. Bu nedenle, her iki proje türü için tüm dosyaları içeren bir şablon dizini oluşturabilirsiniz. Ardından uygulayarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> , projedeki proje veya proje ayarlarının türüne göre görüntülenmemelidir öğeleri gizleyebilirsiniz.  
  
## <a name="filtering-project-items"></a>Proje öğelerini filtreleme  
 `IVsFilterAddProjectItemDlg2` ağaç (sol bölme) ve proje dosyaları (sağ bölme) içindeki öğelerin filtrelenmesini aşağıdaki yollarla sağlar:  
  
- Yerelleştirilmiş adlara göre (. vsdir dosyasında bulunan iletişim kutusunda görüntülenen açıklamalı alt yazılar) tarafından sağlanır `IVsFilterAddProjectItemDlg` .  
  
- Tarafından sunulan disk üzerindeki dosya ve klasörlerin gerçek adlarına (yerelleştirilmemiş —. vsdir dosyası yok) göre `IVsFilterAddProjectItemDlg` .  
  
- Kategoriye göre, tarafından sağlanmaktadır `IVsFilterAddProjectItemDlg2` .  
  
  Kategoriye göre filtrelemek için,. vsdir dosyasındaki bir öğeye bir kategori dizesi sağlayın (örneğin, "Web formu" veya "Istemci öğesi Visual Basic"). İletişim kutusu kodu daha sonra,. vsdir dosyasındaki kategori sınıflandırmasını alır ve size geçirir. Ardından, `IVsFilterAddProjectItemDlg2` **Yeni öğe Ekle** iletişim kutusunu kategorilere göre filtrelemek için bu bilgileri uygulamanıza geçirebilirsiniz. Ayrıca, Web sayfaları için öğeleri veya istemci Win32 uygulaması durumları olarak filtreleyebilirsiniz. Ayrıca, [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] etiketli öğeleri Microsoft Foundation sınıfları (MFC) veya etkin şablon kitaplığı (ATL) öğeleri olarak belirleyebilirsiniz. Bu öğeleri belirlediğinizde, proje sistemi kendi sınıflandırmalarını tanımlayabilir ve böylece sistem Kategoriler ve sınıflandırmalara göre filtrelenebilir.  
  
  Bu filtre işlevini uygularsanız, gizlenmesi gereken her öğenin bir tablosunu eşlemeniz gerekmez. Öğeleri yalnızca türler halinde sınıflandırabilir ve sınıflandırmaları. vsdir dosyasına veya dosyalarına koyabilirsiniz. Daha sonra, belirli bir sınıflandırmayla olan öğelerden herhangi birini, arabirimini uygulayarak gizleyebilirsiniz. Bu şekilde, **Yeni öğe Ekle** iletişim kutusu içindeki öğeleri proje içindeki duruma göre dinamik hale getirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Projeleri genişletmek için genellikle kullanılan nesneler için CATIDs](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Şablon dizin açıklaması (. Vsdir) dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
