---
title: Şablon Dizin Açıklaması (. Vsdir) Dosyalar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16ba609d5b05d565a12b38bd19e9a777851ced5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704696"
---
# <a name="template-directory-description-vsdir-files"></a>Şablon Dizin Açıklaması (.Vsdir) Dosyaları
Şablon dizin açıklama dosyası (.vsdir), tümleşik geliştirme ortamının (IDE) klasörleri, sihirbaz .vsz dosyalarını ve projenizle ilişkili şablon dosyalarını iletişim kutularında görüntülemesini sağlayan bir metin dosyasıdır. İçerik, dosya veya klasör başına bir kayıt içerir. Başvurulan bir konumdaki tüm .vsdir dosyaları birleştirilir, ancak yalnızca bir .vsdir dosyası genellikle birden çok klasör, sihirbaz veya şablon dosyasını açıklamak için sağlanır.

 Klasörler (alt dizinler), .vsdir dosyasında başvurulan dosyalar ve .vsdir dosyasının kendisi aynı dizinde bulunur. IDE sihirbazı çalıştırdığında veya **Yeni Proje'de** bir klasör veya dosya görüntülediğinde veya **Yeni Öğe Ekle** iletişim kutularında, IDE bir .vsdir dosyasının olup olmadığını belirlemek için yürütülen dosyaları içeren dizini inceler. Bir .vsdir dosyası bulunursa, IDE yürütülür veya görüntülenen klasör veya dosya için bir giriş bulunup bulunmadığını belirlemek için dosyayı okur. Bir giriş bulunursa, IDE sihirbazın yürütülmesinde veya içeriğin görüntülenmesinde bilgileri kullanır.

 Aşağıdaki kod örneği \<EnvSDK>\BscPrj\BscPrj\BscPrjProjectItems\Source_Files kayıt defteri anahtarında SourceFiles.vsdir dosyasından:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 Bu durumda, bir dosyada iki kayıt vardır. Yeni bir satır (satır döndürme karakteri) her kaydı ayırır. Her satır farklı bir dosya türünü temsil eder. Bir boru (&#124;) karakteri her kayıttaki alanları ayırır. Tek bir dizin, farklı dosya adları olan birden çok .vsdir dosyası içerebilir veya her dosya türü için bir .vsdir dosyanız olabilir.

## <a name="fields"></a>Alanlar
 Aşağıdaki tabloda her kayıt için belirtilen alanlar listelemektedir.

| Alan | Açıklama |
| - | - |
| Göreli Yol Adı (RelPathName) | HeaderFile.h veya MyWizard.vsz gibi klasörün, şablonun veya .vsz dosyasının adı. Bu alan, bir klasörü temsil etmek için kullanılan bir ad da olabilir. |
| {clsidPackage} | VSPackage'ın uydu dinamik bağlantı kitaplığı (DLL) kaynaklarında Yerelleştirilmiş Ad, Açıklama, IconResourceId ve ÖnerilenBaseName gibi yerelleştirilmiş dizeleri erişimini sağlayan VSPackage GUID. DLLPath sağlanmazsa IconResourceId geçerlidir. **Not:**  Önceki alanlardan biri veya daha fazlası kaynak tanımlayıcısı olmadığı sürece bu alan isteğe bağlıdır. Bu alan genellikle metinlerini yerelleştirmeyen üçüncü taraf sihirbazlarla karşılık gelen .vsdir dosyaları için boştur. |
| Localizedname | Şablon dosyasının veya sihirbazın yerelleştirilmiş adı. Bu alan, "#ResID" formunun bir dize veya kaynak tanımlayıcısı olabilir. Bu **ad, Yeni Öğe Ekle** iletişim kutusunda görüntülenir. **Not:**  LocalizedName bir kaynak tanımlayıcısıysa, {clsidPackage} gereklidir. |
| SıralamaÖnceliği | Bu şablon dosyasının veya sihirbazın göreli önceliğini temsil eden bir tamsayı. Örneğin, bu öğenin değeri 1 ise, bu öğe 1 değeri olan diğer öğelerin yanında ve 2 veya daha büyük bir sıralama değerine sahip tüm öğelerin önünde görüntülenir.<br /><br /> Sıralama önceliği, aynı dizindeki öğelerle görelidir. Aynı dizinde birden fazla .vsdir dosyası olabilir. Bu durumda, tüm öğeleri <em>.</em> bu dizindeki vsdir dosyaları birleştirilir. Aynı önceliğe sahip öğeler, görüntülenen adın karşıtlık sızma lexicographic sırasına göre listelenir. İşlev `_wcsicmp` öğeleri sipariş etmek için kullanılır.<br /><br /> .vsdir dosyalarında tanımlanmamış öğeler, .vsdir dosyalarında listelenen en yüksek öncelik numarasından daha büyük bir öncelik numarası içerir. Sonuç olarak, bu öğeler, adlarına bakılmaksızın görüntülenen listenin sonunda yer almaktadır. |
| Açıklama | Şablon dosyasının veya sihirbazın yerelleştirilmiş açıklaması. Bu alan, "#ResID" formunun bir dize veya kaynak tanımlayıcısı olabilir. Bu **dize,** öğe seçildiğinde Yeni Proje veya Yeni **Öğe Ekle** iletişim kutusunda görünür. |
| DLLPath veya {clsidPackage} | Şablon dosyası veya sihirbaz için bir simge yüklemek için kullanılır. Simge, IconResourceId kullanılarak .dll veya .exe dosyasından kaynak olarak yüklenir. Bu .dll veya .exe dosyası tam bir yol kullanılarak veya bir VSPackage GUID kullanılarak tanımlanabilir. VSPackage uygulama DLL simgesi (uydu DLL değil) yüklemek için kullanılır. |
| IconResourceId | Görüntülenecek simgeyi belirleyen DLL veya VSPackage uygulama DLL'deki kaynak tanımlayıcısı. |
| Bayraklar<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>( ) | **Yeni Öğe Ekle** iletişim kutusundaki **Ad** ve **Konum** alanlarını devre dışı bırakıp etkinleştirmek için kullanılır. **Bayraklar** alanının değeri, gerekli bit bayraklarının birleşiminin ondalık eşdeğeridir.<br /><br /> Kullanıcı **Yeni** sekmesinde bir öğe seçtiğinde, proje Ad alanı nın ve Konum alanının **Yeni Öğe Ekle** iletişim kutusu ilk görüntülendiğinde gösterip gösterilmediğini belirler. Bir öğe, .vsdir dosyası aracılığıyla, yalnızca alanların etkinleştirilip etkinleştirilmediğini ve öğe seçildiğinde devre dışı bırakıldığını denetleyebilir. |
| ÖnerilenBaseName | Dosya, sihirbaz veya şablon için varsayılan adı temsil eder. Bu alan, "#ResID" formunun bir dize veya kaynak tanımlayıcısıdır. IDE, öğe için varsayılan bir ad sağlamak için bu değeri kullanır. Bu temel değer, myFile21.asp gibi adı benzersiz kılmak için bir tamsayı değeriyle eklenir.<br /><br /> Önceki listede, Açıklama, DLLPath, IconResourceId, Bayraklar ve ÖnerilenBaseNumber yalnızca şablon ve sihirbaz dosyaları için geçerlidir. Bu alanlar klasörler için geçerli değildir. Bu gerçek, \<EnvSDK>\BscPrj\BscPrj\BscPrj\BscPrjProjectItems kayıt defteri anahtarındaki BscPrjProjectItems dosyasındaki kodda gösterilmiştir. Bu dosya, her kayıt için dört alana sahip üç kayıt (her klasör için bir tane) içerir: RelPathName, {clsidPackage}, LocalizedName ve SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Sihirbaz dosyası oluşturduğunuzda, aşağıdaki sorunları da göz önünde bulundurmanız gerekir.

- Anlamlı veri bulunmayan gerekli olmayan herhangi bir alan, yer tutucu olarak 0 (sıfır) içermelidir.

- Yerelleştirilmiş ad sağlanmadıysa, sihirbaz dosyasında göreli yol adı kullanılır.

- DLLPath simge konumu için clsidPackage geçersiz kılar.

- Simge tanımlanmamışsa, IDE varsayılan simgeyi bu uzantıya sahip bir dosyanın yerine alır.

- Önerilen temel ad sağlanmazsa, 'Project' kullanılır.

- .vsz dosyalarını, klasörlerini veya şablon dosyalarını silerseniz, ilişkili kayıtlarını da .vsdir dosyasından kaldırmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
