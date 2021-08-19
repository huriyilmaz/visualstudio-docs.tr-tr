---
title: Şablon dizin açıklaması (. Vsdir) dosyaları | Microsoft Docs
description: şablon dizin açıklama dosyasının, Visual Studio ıde 'nin proje ile ilişkili klasörleri,. vsz dosyalarını ve şablonları görüntülemesini nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 01ecd11c47edf00fb6e7126d496bb55c24f74973
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158833"
---
# <a name="template-directory-description-vsdir-files"></a>Şablon Dizin Açıklaması (.Vsdir) Dosyaları
Şablon dizin açıklama dosyası (. vsdir), tümleşik geliştirme ortamının (IDE), iletişim kutularındaki projenizle ilişkili klasörleri, sihirbaz. vsz dosyalarını ve şablon dosyalarını görüntülemesini sağlayan bir metin dosyasıdır. İçerikler dosya veya klasör başına bir kayıt içerir. Başvurulan bir konumdaki tüm. VSDir dosyaları birleştirilir, ancak birden çok klasörü, Sihirbazı veya şablon dosyasını anlatmak için genellikle yalnızca bir. vsdir dosyası sağlanır.

 Klasörler (alt dizinler),. vsdir dosyasında başvurulan dosyalar ve. vsdir dosyası aynı dizinde bulunur. ıde bir sihirbaz çalıştırdığında veya **yeni Project** veya **yeni öğe ekle** iletişim kutularında bir klasör veya dosya görüntülediğinde, ıde, bir. vsdir dosyasının mevcut olup olmadığını anlamak için yürütülen dosyaları içeren dizini inceler. Bir. vsdir dosyası bulunursa, IDE onu yürütülen veya görüntülenmiş klasör ya da dosya için bir giriş içerip içermediğini anlamak üzere okur. Bir giriş bulunursa IDE, sihirbazın yürütüldüğü veya içeriğin görüntülendiği bilgileri kullanır.

 Aşağıdaki kod örneği, \<EnvSDK> \Bscprj\bscprj\bscprjprojectıtems\ Source_Files kayıt defteri anahtarındaki SourceFiles. vsdir dosyasından verilmiştir:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 Bu durumda, iki kayıt tek bir dosyadır. Yeni bir satır (satır başı karakter) her kaydı ayırır. Her satır, farklı bir dosya türünü temsil eder. Bir kanal (&#124;) karakteri her kayıttaki alanları ayırır. Tek bir dizin, farklı dosya adlarına sahip birden fazla. vsdir dosyası içerebilir veya her dosya türü için bir. vsdir dosyasına sahip olabilirsiniz.

## <a name="fields"></a>Alanlar
 Aşağıdaki tabloda her kayıt için belirtilen alanlar listelenmektedir.

| Alan | Açıklama |
| - | - |
| Göreli yol adı (RelPathName) | Üstbilgi dosyası. h veya MyWizard. vsz gibi klasör, şablon veya. vsz dosyasının adı. Bu alan ayrıca bir klasörü temsil etmek için kullanılan bir ad olabilir. |
| {clsidPackage} | VSPackage 'in uydu dinamik bağlantı kitaplığı (DLL) kaynaklarında LocalizedName, Description, ıresourceıd ve SuggestedBaseName gibi yerelleştirilmiş dizelere erişim sağlayan VSPackage GUID 'SI. DLLPath sağlanmazsa, ıresourceıd geçerlidir. **Note:**  Önceki alanlardan biri veya daha fazlası kaynak tanımlayıcısı değilse bu alan isteğe bağlıdır. Bu alan, kendi metinlerini yerelleştirmez üçüncü taraf sihirbazlarıyla karşılık gelen. VSDir dosyaları için genellikle boştur. |
| LocalizedName | Şablon dosyasının veya sihirbazının yerelleştirilmiş adı. Bu alan, "#ResID" biçiminde bir dize veya kaynak tanımlayıcısı olabilir. Bu ad, **Yeni öğe Ekle** iletişim kutusunda görüntülenir. **Note:**  LocalizedName bir kaynak tanımsıdır, {clsidPackage} gerekir. |
| SortPriority | Bu şablon dosyasının veya sihirbazının göreli önceliğini temsil eden bir tamsayı. Örneğin, bu öğenin değeri 1 ise bu öğe, 1 değerine sahip diğer öğelerin yanında görüntülenir ve 2 veya daha büyük bir sıralama değeri olan tüm öğelerin ilerisindedir.<br /><br /> Sıralama önceliği, aynı dizindeki öğelere göre belirlenir. Aynı dizinde birden fazla. vsdir dosyası olabilir. Bu durumda, tüm öğeleri <em>.</em> Bu dizindeki VSDir dosyaları birleştirilir. Aynı önceliğe sahip öğeler görüntülenen adının büyük/küçük harf duyarsız lexicographic sırasıyla listelenir. `_wcsicmp`İşlevi öğeleri sıralamak için kullanılır.<br /><br /> . Vsdir dosyalarında açıklanmayan öğeler,. vsdir dosyalarında listelenen en yüksek öncelik numarasından daha büyük bir öncelik numarası içerir. Sonuç, bu öğelerin, adından bağımsız olarak görüntülenen listenin sonunda olması olur. |
| Açıklama | Şablon dosyasının veya sihirbazının yerelleştirilmiş açıklaması. Bu alan, "#ResID" biçiminde bir dize veya kaynak tanımlayıcısı olabilir. bu dize, öğe seçildiğinde **yeni Project** veya **yeni öğe ekle** iletişim kutusunda görünür. |
| DLLPath veya {clsidPackage} | Şablon dosyası veya sihirbazına yönelik bir simge yüklemek için kullanılır. Simge, ıresourceıd kullanarak bir .dll veya .exe dosyasından kaynak olarak yüklenir. Bu .dll veya .exe dosyası, tam yol kullanılarak veya VSPackage 'un GUID 'SI kullanılarak belirlenebilir. VSPackage 'ın uygulama DLL 'SI, simgenin (uydu DLL değil) yüklenmesi için kullanılır. |
| Iresourceıd | DLL veya VSPackage uygulama DLL dosyasında görüntülenecek simgeyi belirleyen kaynak tanımlayıcısı. |
| Flags ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS> ) | **Yeni öğe Ekle** Iletişim kutusundaki **ad** ve **konum** alanlarını devre dışı bırakmak veya etkinleştirmek için kullanılır. **Flags** alanının değeri, gerekli bit bayrakları birleşiminin ondalık eşdeğeridir.<br /><br /> Kullanıcı **Yeni** sekmede bir öğe seçtiğinde proje, **Yeni öğe Ekle** Iletişim kutusu ilk görüntülendiğinde ad alanının ve konum alanının gösterilip gösterilmeyeceğini belirler. Bir. vsdir dosyası aracılığıyla, öğe seçildiğinde yalnızca alanların etkin ve devre dışı olarak devre dışı bırakılıp bırakılmadığını kontrol edebilir. |
| SuggestedBaseName | Dosya, sihirbaz veya şablon için varsayılan adı temsil eder. Bu alan, "#ResID" formunun bir dize veya kaynak tanımlayıcısıdır. IDE, öğe için varsayılan bir ad sağlamak üzere bu değeri kullanır. Bu taban değeri, MyFile21. asp gibi benzersiz bir tamsayı değeri olacak şekilde eklenir.<br /><br /> Önceki listede, Description, DLLPath, ıresourceıd, Flags ve Mülatedbasenumarası yalnızca şablon ve sihirbaz dosyaları için geçerlidir. Bu alanlar klasörler için geçerlidir. Bu olgu, \<EnvSDK> \BscPrj\BscPrj\BscPrjProjectItems kayıt defteri anahtarındaki BscPrjProjectItems dosyasındaki kodda gösterilmiştir. Bu dosya, her bir kayıt için dört alan içeren üç kayıt (her bir klasör için bir adet) içerir: RelPathName, {Clsıdpackage}, LocalizedName ve SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Bir sihirbaz dosyası oluşturduğunuzda, aşağıdaki sorunları da göz önünde bulundurmanız gerekir.

- Anlamlı veri olmayan hiçbir gerekli olmayan alan, yer tutucu olarak 0 (sıfır) içermelidir.

- Yerelleştirilmiş ad sağlanmazsa, ilgili yol adı sihirbaz dosyasında kullanılır.

- DLLPath, simge konumu için Clsıdpackage 'i geçersiz kılar.

- Hiçbir simge tanımlanmamışsa, IDE bu uzantıya sahip bir dosya için varsayılan simgenin yerini alır.

- önerilen temel ad sağlanmazsa, ' Project ' kullanılır.

- . Vsz dosyalarını, klasörlerini veya şablon dosyalarını silerseniz, ilişkili kayıtlarını. vsdir dosyasından de kaldırmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
