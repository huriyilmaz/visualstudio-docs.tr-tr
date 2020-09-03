---
title: Hizmet Başvurusu Yapılandırma İletişim Kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f5bae3acb6f687c8c787e2d4121999d1133b0f1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586932"
---
# <a name="configure-service-reference-dialog-box"></a>Hizmet Başvurusu Yapılandır iletişim kutusu

**Hizmet başvurusunu Yapılandır** iletişim kutusu, WINDOWS COMMUNICATION FOUNDATION (WCF) hizmetlerinin davranışını yapılandırmanızı sağlar.

**Hizmet başvurusunu Yapılandır** iletişim kutusuna erişmek için **Çözüm Gezgini** bir hizmet başvurusunu sağ tıklatın ve **hizmet başvurusunu Yapılandır**' ı seçin. İletişim kutusuna, **hizmet başvurusu Ekle Iletişim kutusunda** **Gelişmiş** düğmesine tıklayarak da erişebilirsiniz.

## <a name="task-list"></a>Görev listesi

- Bir WCF hizmetinin barındırıldığı adresi değiştirmek için **Adres** alanına yeni adresi girin.

- Bir WCF istemcisindeki sınıfların erişim düzeyini değiştirmek için, **oluşturulan sınıflar Için erişim düzeyi** listesinde bir erişim düzeyi anahtar sözcüğü seçin.

- WCF hizmetinin yöntemlerini zaman uyumsuz olarak çağırmak için **zaman uyumsuz Işlemler oluştur** onay kutusunu seçin.

- Bir WCF istemcisinde ileti sözleşmesi türleri oluşturmak için **her zaman ileti sözleşmeleri oluştur** onay kutusunu seçin.

- Bir WCF istemcisi için liste veya sözlük koleksiyon türlerini belirtmek için, **koleksiyon türü** ve **sözlük koleksiyon türü** listelerinden türleri seçin.

- Tür paylaşımını devre dışı bırakmak için, **başvurulan derlemelerde türleri yeniden kullan** onay kutusunu temizleyin. Başvurulan derlemelerin bir alt kümesi için tür paylaşımını etkinleştirmek üzere, **başvurulan derlemelerde türleri yeniden kullan** onay kutusunu seçin, **belirtilen başvurulan derlemelerdeki türleri yeniden kullan**' ı seçin ve **başvurulan derlemeler listesinde**istenen başvuruları seçin.

## <a name="uielement-list"></a>UIElement listesi

**Adres**

Hizmet başvurusunun bir hizmet için aradığı Web adresini güncelleştirir. Örneğin, geliştirme sırasında hizmet bir geliştirme sunucusunda barındırılabilir ve daha sonra bir üretim sunucusuna taşınabilir ve bir adres değişikliği tasarımda.

> [!NOTE]
> Adres öğesi, **hizmet başvurusu Ekle Iletişim kutusundan** **hizmet başvurusunu Yapılandır** iletişim kutusu görüntülendiğinde kullanılamaz.

**Oluşturulan sınıflar için erişim düzeyi**

WCF istemci sınıfları için kod erişim düzeyini belirler.

> [!NOTE]
> Web sitesi projeleri için, bu seçenek her zaman olarak ayarlanır `Public` ve değiştirilemez. Daha fazla bilgi için bkz. [hizmet başvurularına sorun giderme](../data-tools/troubleshooting-service-references.md).

**Zaman uyumsuz işlemler oluşturma**

WCF hizmeti yöntemlerinin zaman uyumlu olarak mı (varsayılan) yoksa zaman uyumsuz olarak mı çağrıldığını belirler.

**Görev tabanlı işlemler oluştur**

Async kodu yazarken, bu seçenek .NET 4 ile tanıtılan görev paralel kitaplığı (TPL) avantajlarından yararlanmanıza olanak sağlar. Bkz. [görev paralel kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

**Her zaman ileti sözleşmeleri oluştur**

Bir WCF istemcisi için ileti anlaşması türlerinin oluşturulup oluşturulmayacağını belirler. İleti sözleşmeleri hakkında daha fazla bilgi için bkz. [ileti sözleşmelerini kullanma](/dotnet/framework/wcf/feature-details/using-message-contracts).

**Koleksiyon türü**

Bir WCF istemcisi için liste koleksiyonu türünü belirtir. Varsayılan tür <xref:System.Array> .

**Sözlük toplama türü**

Bir WCF istemcisi için sözlük koleksiyonu türünü belirtir. Varsayılan tür <xref:System.Collections.Generic.Dictionary%602> .

**Başvurulan derlemelerdeki türleri yeniden kullan**

Bir WCF istemcisinin, bir hizmet eklendiğinde veya güncelleştirilirken yeni türler oluşturmak yerine, başvurulan derlemelerde mevcut olan öğeleri yeniden kullanmayı deneip denemeyeceğini belirler. Varsayılan olarak, bu seçenek denetlenir.

**Tüm başvurulan derlemelerdeki türleri yeniden kullan**

Seçildiğinde, **başvurulan derlemeler listesindeki** tüm türler mümkünse yeniden kullanılır. Varsayılan olarak, bu seçenek seçilidir.

**Belirtilen başvurulan derlemelerdeki türleri yeniden kullan**

Seçildiğinde, yalnızca **başvurulan derlemeler listesindeki** seçili türler yeniden kullanılır.

**Başvurulan derlemeler listesi**

Proje veya Web sitesi için başvurulan derlemelerin bir listesini içerir. **Belirtilen başvurulan derlemelerdeki türleri yeniden kullan**' ı seçtiğinizde, bireysel derlemeleri seçebilir veya temizleyebilirsiniz.

**Web başvurusu Ekle**

**Web başvurusu Ekle** iletişim kutusunu görüntüler.

> [!NOTE]
> Bu seçenek yalnızca .NET Framework sürüm 2,0 ' i hedefleyen projeler için kullanılmalıdır.
>
> [!NOTE]
> **Web başvurusu Ekle** düğmesi yalnızca **hizmet başvurusu Ekle Iletişim kutusundan** **hizmet başvurusunu Yapılandır** iletişim kutusu görüntülendiğinde kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: bir Web hizmetine başvuru ekleme](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/configure-service-reference-dialog-box.md)
