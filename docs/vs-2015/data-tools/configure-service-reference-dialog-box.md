---
title: Hizmet başvurusunu yapılandırma Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac8f4cf619bbdd007bb7aa570f549ae3c0b50e86
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651107"
---
# <a name="configure-service-reference-dialog-box"></a>Hizmet Başvurusu Yapılandırma İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Hizmet başvurusunu Yapılandır** iletişim kutusu, [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] hizmetlerinin davranışını yapılandırmanızı sağlar.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden Içeri ve dışarı aktarma ayarları ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Hizmet başvurusunu Yapılandır** iletişim kutusuna erişmek için **Çözüm Gezgini** bir hizmet başvurusunu sağ tıklatın ve **hizmet başvurusunu Yapılandır**' ı seçin. İletişim kutusuna, **hizmet başvurusu Ekle Iletişim kutusunda** **Gelişmiş** düğmesine tıklayarak da erişebilirsiniz.

## <a name="task-list"></a>Görev Listesi

- Bir WCF hizmetinin barındırıldığı adresi değiştirmek için **Adres** alanına yeni adresi girin.

- Bir WCF istemcisindeki sınıfların erişim düzeyini değiştirmek için, **oluşturulan sınıflar Için erişim düzeyi** listesinde bir erişim düzeyi anahtar sözcüğü seçin.

- WCF hizmetinin yöntemlerini zaman uyumsuz olarak çağırmak için **zaman uyumsuz Işlemler oluştur** onay kutusunu seçin.

- Bir WCF istemcisinde ileti sözleşmesi türleri oluşturmak için **her zaman ileti sözleşmeleri oluştur** onay kutusunu seçin.

- Bir WCF istemcisi için liste veya sözlük koleksiyon türlerini belirtmek için, **koleksiyon türü** ve **sözlük koleksiyon türü** listelerinden türleri seçin.

- Tür paylaşımını devre dışı bırakmak için, **başvurulan derlemelerde türleri yeniden kullan** onay kutusunu temizleyin. Başvurulan derlemelerin bir alt kümesi için tür paylaşımını etkinleştirmek üzere, **başvurulan derlemelerde türleri yeniden kullan** onay kutusunu seçin, **belirtilen başvurulan derlemelerdeki türleri yeniden kullan**' ı seçin ve başvurulan başvuruları seçin  **bütünleştirilmiş kodlar listesi**.

## <a name="uielement-list"></a>UIElement Listesi
 **Adres** Hizmet başvurusunun hizmet için aradığı Web adresini güncelleştirmek için kullanılır. Örneğin, geliştirme sırasında hizmet bir geliştirme sunucusunda barındırılabilir ve daha sonra bir üretim sunucusuna taşınabilir ve bir adres değişikliği tasarımda.

> [!NOTE]
> Adres öğesi, **hizmet başvurusu Ekle Iletişim kutusundan** **hizmet başvurusunu Yapılandır** iletişim kutusu görüntülendiğinde kullanılamaz.

 **Oluşturulan sınıflar Için erişim düzeyi** WCF istemci sınıfları için kod erişim düzeyini belirler.

> [!NOTE]
> Web sitesi projeleri için, bu seçenek her zaman `Public` olarak ayarlanır ve değiştirilemez. Daha fazla bilgi için bkz. [hizmet başvurularına sorun giderme](../data-tools/troubleshooting-service-references.md).

 **Zaman uyumsuz Işlemler oluşturma** WCF hizmeti yöntemlerinin zaman uyumlu olarak mı (varsayılan) yoksa zaman uyumsuz olarak mı çağracağını belirler.

 **Görev tabanlı Işlemler oluştur** Zaman uyumsuz kod yazarken bu seçenek, .NET 4 ile tanıtılan görev paralel kitaplığı (TPL) avantajlarından yararlanmanızı sağlar. Bkz. [görev paralel kitaplığı (TPL)](https://msdn.microsoft.com/library/dd460717.aspx).

 **Her zaman ileti sözleşmeleri oluştur** Bir WCF istemcisi için ileti sözleşmesi türlerinin oluşturulup oluşturulmayacağını belirler. İleti sözleşmeleri hakkında daha fazla bilgi için bkz. [Ileti sözleşmelerini kullanma](https://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).

 **Koleksiyon türü** Bir WCF istemcisi için liste koleksiyonu türünü belirtir. Varsayılan tür <xref:System.Array>.

 **Sözlük toplama türü** Bir WCF istemcisi için sözlük koleksiyonu türünü belirtir. Varsayılan tür <xref:System.Collections.Generic.Dictionary%602>.

 **Başvurulan derlemelerdeki türleri yeniden kullan** Bir hizmet eklendiğinde veya güncelleştirilirken yeni türler oluşturmak yerine, bir WCF istemcisinin, başvurulan derlemelerde zaten mevcut olan yeniden kullanmayı deneyip denemeyeceğini belirler. Varsayılan olarak, bu seçenek denetlenir.

 **Tüm başvurulan derlemelerdeki türleri yeniden kullan** Seçildiğinde, **başvurulan derlemeler listesindeki** tüm türler mümkünse yeniden kullanılacaktır. Varsayılan olarak, bu seçenek seçilidir.

 **Belirtilen başvurulan derlemelerdeki türleri yeniden kullan** Seçildiğinde, yalnızca **başvurulan derlemeler listesindeki** seçili türler yeniden kullanılır.

 **Başvurulan derlemeler listesi** Proje veya Web sitesi için başvurulan derlemelerin bir listesini içerir. **Belirtilen başvurulan derlemelerdeki türleri yeniden kullan** seçildiğinde, bireysel derlemeler seçilebilir veya temizlenemez.

 **Web başvurusu Ekle** [Nib: Web başvurusu Ekle Iletişim kutusunu](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)görüntüler.

> [!NOTE]
> Bu seçenek yalnızca [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürüm 2,0 ' i hedefleyen projeler için kullanılmalıdır.

> [!NOTE]
> **Web başvurusu Ekle** düğmesi yalnızca **hizmet başvurusu Ekle Iletişim kutusundan** **hizmet başvurusunu Yapılandır** iletişim kutusu görüntülendiğinde kullanılabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: hizmet başvurusu ekleme, güncelleştirme veya kaldırma](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9) [nasıl yapılır: bir Web hizmetine başvuru ekleme](https://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168) [Windows Communication Foundation Hizmetleri ve WCF veri Hizmetleri](../data-tools/configure-service-reference-dialog-box.md)
