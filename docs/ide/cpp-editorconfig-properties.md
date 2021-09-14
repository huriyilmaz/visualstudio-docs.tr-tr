---
title: C++ EditorConfig biçimlendirme kuralları
titleSuffix: ''
description: Visual Studio'de C++ kodunu biçimlendirmek için EditorConfig'i kullanma hakkında Visual Studio.
ms.date: 9/14/2020
author: jureid
ms.author: jureid
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CPP
ms.prod: visual-studio-windows
ms.topic: reference
ms.workload:
- cplusplus
monikerRange: vs-2019
ms.openlocfilehash: b7554e2038f0be8d72b96e8b53280faca498e772
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628826"
---
# <a name="c-editorconfig-formatting-conventions"></a>C++ EditorConfig biçimlendirme kuralları

C++ Visual Studio biçimlendiren, genel olarak uygulanabilir zengin bir yapılandırılabilir ayarlar kümesine sahip. Belirli bir çalışma alanı için C++ biçimlendirme ayarlarını ayarlamak üzere [clangformat veya](https://clang.llvm.org/docs/ClangFormat.html) [EditorConfig kullanın.](https://editorconfig.org/) Hem Visual Studio hem de Visual Studio Code C++ biçimlendirme ayarlarının her biri için yerleşik EditorConfig desteğine ve EditorConfig ayarları öncelikli olacak şekilde Visual Studio'ye sahip olur. Bu, C++ biçimlendirmesini daha ayrıntılı bir düzeyde yapılandırmak ve projeye katkıda bulunan herkes için tutarlı kod stili uygulamak için çalışma alanınıza EditorConfig dosyaları eklebilirsiniz.

## <a name="c-formatting-conventions"></a>C++ biçimlendirme kuralları

C++ biçimlendirme EditorConfig ayarları ön eki ile birlikte `cpp_` kullanılır. EditorConfig dosyanız aşağıdaki gibi olabilir:

```ini
[*.{c++,cc,cpp,cxx,h,h++,hh,hpp,hxx,inl,ipp,tlh,tli}]

cpp_indent_case_contents_when_block = true
cpp_new_line_before_open_brace_namespace = same_line
```

Bu belgenin geri kalanında, Visual Studio ve VS Code tarafından desteklenen tüm EditorConfig C++ biçimlendirme ayarları VS Code.

### <a name="indentation-settings"></a>Girintileme ayarları

**Girinti ayraçları**

- Ad: `cpp_indent_braces`
- Değerler: `true` , `false`

**Her satırı göreli olarak girintileme**

- Ad: `cpp_indent_multi_line_relative_to`
- Değerler:
  - `outermost_parenthesis` - Yeni bir satır yazıldı mı, göreli olarak en dıştaki açık paranteze girintili olarak eklenir.
  - `innermost_parenthesis` - Yeni bir satır yazgınca, en içteki açık paranteze göre girintili olur.
  - `statement_begin` - Yeni bir satır yazgınca, geçerli deyimin başlangıcına göre girintili olarak girintili olarak eklenir.

**Parantez içinde, yeni satırları yazarak hizala**

- Ad: `cpp_indent_within_parentheses`
- Değerler:
  - `align_to_parenthesis` - İçeriği parantez açmak için hizala.
  - `indent` - Yeni satırları girintileme.

**Mevcut kodda, yeni satırları parantez içinde hizalamak için ayarını kullanma**

- Ad: `cpp_indent_preserve_within_parentheses`
- Değerler: `true` , `false`

**Büyük/büyük/büyük harf içeriklerini girintileme**

- Ad: `cpp_indent_case_contents`
- Değerler: `true` , `false`

**Büyük/büyük/harf etiketlerini girintileme**

- Ad: `cpp_indent_case_labels`
- Değerler: `true` , `false`

**Bir case deyiminden sonra küme ayraçlarını girintileme**

- Ad: `cpp_indent_case_contents_when_block`
- Değerler: `true` , `false`

**Parametre olarak kullanılan lambdaların girinti ayraçları**

- Ad: `cpp_indent_lambda_braces_when_parameter`
- Değerler: `true` , `false`

**Etiketlerin konumu**

- Ad: `cpp_indent_goto_labels`
- Değerler:
  - `one_left` - Sol tarafta bir girinti
  - `leftmost_column` - En soldaki sütuna taşıma
  - `none` - Girintili bırakın

**Ön işlemci yönergelerinin konumu**

- Ad: `cpp_indent_preprocessor`
- Değerler:
  - `one_left` - Sol tarafta bir girinti
  - `leftmost_column` - En soldaki sütuna taşıma
  - `none` - Girintili bırakın

**Erişim belirleyicilerini girintileme**

- Ad: `cpp_indent_access_specifiers`
- Değerler: `true` , `false`

**Ad alanı içeriğini girintileme**

- Ad: `cpp_indent_namespace_contents`
- Değerler: `true` , `false`

**Açıklama girintisini koruma**

- Ad: `cpp_indent_preserve_comments`
- Değerler: `true` , `false`

### <a name="newline-settings"></a>Yeni satır ayarları

**Ad alanları için açık ayraçların konumu**

- Ad: `cpp_new_line_before_open_brace_namespace`
- Değerler:
  - `new_line` - Yeni satıra taşıma
  - `same_line` - Aynı satırda tut ama önce bir boşluk ekleyin
  - `ignore` - Otomatik olarak yeniden konumlandırma

**Türler için açık ayraçların konumu**

- Ad: `cpp_new_line_before_open_brace_type`
- Değerler:
  - `new_line` - Yeni satıra taşıma
  - `same_line` - Aynı satırda tut ama önce bir boşluk ekleyin
  - `ignore` - Otomatik olarak yeniden konumlandırma

**İşlevler için açık ayraçların konumu**

- Ad: `cpp_new_line_before_open_brace_function`
- Değerler:
  - `new_line` - Yeni satıra taşıma
  - `same_line` - Aynı satırda tut ama önce bir boşluk ekleyin
  - `ignore` - Otomatik olarak yeniden konumlandırma

**Denetim blokları için açık ayraçların konumu**

- Ad: `cpp_new_line_before_open_brace_block`
- Değerler:
  - `new_line` - Yeni satıra taşıma
  - `same_line` - Aynı satırda tut ama önce bir boşluk ekleyin
  - `ignore` - Otomatik olarak yeniden konumlandırma

**Lambdalar için açık ayraçların konumu**

- Ad: `cpp_new_line_before_open_brace_lambda`
- Değerler:
  - `new_line` - Yeni satıra taşıma
  - `same_line` - Aynı satırda tut ama önce bir boşluk ekleyin
  - `ignore` - Otomatik olarak yeniden konumlandırma
 
**Kapsam ayraçlarını ayrı satırlara yer**

- Ad: `cpp_new_line_scope_braces_on_separate_lines`
- Değerler: `true` , `false`

**Boş türler için, kapatma ayraçlarını açma ayraçları ile aynı satıra taşıma**

- Ad: `cpp_new_line_close_brace_same_line_empty_type`
- Değerler: `true` , `false`

**Boş işlev gövdeleri için kapatma ayraçlarını açma ayraçları ile aynı satıra taşıma**

- Ad: `cpp_new_line_close_brace_same_line_empty_function`
- Değerler: `true` , `false`

**' Catch ' ve benzer anahtar sözcükleri yeni bir satıra yerleştir**

- Ad: `cpp_new_line_before_catch`
- Değerler: `true` , `false`

**' Else ' öğesini yeni bir satıra yerleştir**

- Ad: `cpp_new_line_before_else`
- Değerler: `true` , `false`

**Do-while döngüsünde yeni bir satıra ' while ' yerleştir**

- Ad: `cpp_new_line_before_while_in_do_while`
- Değerler: `true` , `false`

### <a name="spacing-settings"></a>Aralık ayarları

**İşlev adları ve bağımsız değişken listelerinin açılış ayraçları arasındaki boşluk**

- Ad: `cpp_space_before_function_open_parenthesis`
- Değerler:
  - `insert` -Bir boşluk ekleyin
  - `remove` -Boşlukları kaldır
  - `ignore` -Boşlukları değiştirme

**Bağımsız değişken listesinin parantezleri içine boşluk Ekle**

- Ad `cpp_space_within_parameter_list_parentheses` değerleri: `true` , `false`

**Bağımsız değişken listesi boş olduğunda parantezler arasında boşluk Ekle**

- Ad: `cpp_space_between_empty_parameter_list_parentheses`
- Değerler: `true` , `false`

**Denetim akışı deyimlerinde anahtar sözcük ve açma ayracı arasına boşluk Ekle**

- Ad: `cpp_space_after_keywords_in_control_flow_statements`
- Değerler: `true` , `false`

**Denetim ifadesinin parantezleri içinde boşluk Ekle**

- Ad: `cpp_space_within_control_flow_statement_parentheses`
- Değerler: `true` , `false`

**Lambda bağımsız değişken listelerinin açılış ayracından önce boşluk Ekle**

- Ad: `cpp_space_before_lambda_open_parenthesis`
- Değerler: `true` , `false`

**C stili tür dönüştürmenin parantezleri içinde boşluk Ekle**

- Ad: `cpp_space_within_cast_parentheses`
- Değerler: `true` , `false`

**C stili tür dönüştürmenin kapatma parantezinden sonra boşluk Ekle**

- Ad: `cpp_space_after_cast_close_parenthesis`
- Değerler: `true` , `false`

**Parantez içine alınmış bir ifadenin parantezleri içinde boşluk Ekle**

- Ad: `cpp_space_within_expression_parentheses`
- Değerler: `true` , `false`

**Blok ayracını açmadan önce boşluk Ekle**

- Ad: `cpp_space_before_block_open_brace`
- Değerler: `true` , `false`

**Boş küme ayraçları arasında boşluk Ekle**

- Ad: `cpp_space_between_empty_braces`
- Değerler: `true` , `false`

**Tek düzen başlatma ve Başlatıcı listelerinin ayracını açmadan önce boşluk Ekle**

- Ad: `cpp_space_before_initializer_list_open_brace`
- Değerler: `true` , `false`

**Tek düzen başlatma ve Başlatıcı listelerinin küme ayraçları içine boşluk Ekle**

- Ad: `cpp_space_within_initializer_list_braces`
- Değerler: `true` , `false`

**Tek düzen başlatma ve başlatıcı listeleri içindeki boşlukları koru**

- Ad: `cpp_space_preserve_in_initializer_list`
- Değerler: `true` , `false`

**Açma köşeli ayracından önce boşluk Ekle**

- Ad: `cpp_space_before_open_square_bracket`
- Değerler: `true` , `false`

**Köşeli ayraç içine boşluk Ekle**

- Ad: `cpp_space_within_square_brackets`
- Değerler: `true` , `false`

**Boş köşeli ayraçlardan önce boşluk Ekle**

- Ad: `cpp_space_before_empty_square_brackets`
- Değerler: `true` , `false`

**Boş köşeli ayraç arasına boşluk Ekle**

- Ad: `cpp_space_between_empty_square_brackets`
- Değerler: `true` , `false`

**Çok boyutlu diziler için köşeli ayraçları Gruplandır**

- Ad: `cpp_space_group_square_brackets`
- Değerler: `true` , `false`

**Lambdalar için köşeli ayraç içine boşluk Ekle**

- Ad: `cpp_space_within_lambda_brackets`
- Değerler: `true` , `false`

**Spacebetweenemptylambdavköşeli ayraç**

- Ad: `cpp_space_between_empty_lambda_brackets`
- Değerler: `true` , `false`

**Virgüllerden önce boşluk Ekle**

- Ad: `cpp_space_before_comma`
- Değerler: `true` , `false`

**Virgüllerden sonra boşluk Ekle**

- Ad: `cpp_space_after_comma`
- Değerler: `true` , `false`

**Üye işleçlerden önce ve sonra boşlukları kaldır**

- Ad: `cpp_space_remove_around_member_operators`
- Değerler: `true` , `false`

**Tür bildirimlerinde taban için iki noktadan önce boşluk Ekle**

- Ad: `cpp_space_before_inheritance_colon`
- Değerler: `true` , `false`

**Oluşturucular için iki noktadan önce boşluk Ekle**

- Ad: `cpp_space_before_constructor_colon`
- Değerler: `true` , `false`

**Noktalı virgüllerden önce boşluğu kaldır**

- Ad: `cpp_space_remove_before_semicolon`
- Değerler: `true` , `false`

**Noktalı virgülden sonra boşluk Ekle**

- Ad: `cpp_space_after_semicolon`
- Değerler: `true` , `false`

**Birli İşleçler ve işlenenleri arasındaki boşlukları kaldır**

- Ad: `cpp_space_remove_around_unary_operator`
- Değerler: `true` , `false`

**İkili işleçler için boşluk**

- Ad: `cpp_space_around_binary_operator`
- Değerler:
  - `insert` - İkili işleçlerin önce ve sonra boşluklarını ekler.
  - `remove` - İkili işleçlerin çevresindeki boşlukları kaldırır.
  - `ignore` - İkili işleçlerin çevresindeki boşlukları değiştirme.

**Atama işleçleri için boşluk**

- Ad: `cpp_space_around_assignment_operator`
- Değerler:
  - `insert` - Atama işleçleri çevreye boşluklar ekler.
  - `remove` - Atama işleçleri çevresindeki boşlukları kaldırır.
  - `ignore` - Atama işleçleri çevresindeki alanları değiştirme.

**İşaretçi/başvuru hizalaması**

- Ad: `cpp_space_pointer_reference_alignment`
- Değerler:
  - `left` - Sola hizala.
  - `center` - Ortayı hizala.
  - `right` - Sağa hizala.
  - `ignore` - Değişmeden bırakın.

**Koşullu işleçler için boşluk**

- Ad: `cpp_space_around_ternary_operator`
- Değerler:
  - `insert` - Koşullu işleçlerin etrafına boşluklar ekler.
  - `remove` - Koşullu işleçlerin çevresindeki boşlukları kaldırır.
  - `ignore` - Koşullu işleçlerin çevresindeki boşlukları değiştirme.

### <a name="wrapping-options"></a>Sarmalama seçenekleri

**Bloklar için sarmalama seçenekleri**

- Ad: `cpp_wrap_preserve_blocks`
- Değerler:
  - `one_liners` - Tek satırlı kod bloklarını sarmalayın.
  - `all_one_line_scopes` - Sonraki satırda açma ve kapatma ayraçlarının bulunduğu kod bloklarını sarmalayın.
  - `never` - Bloklar için her zaman Yeni Satırlar ayarlarını uygula.

## <a name="see-also"></a>Ayrıca bkz.

- [EditorConfig.org](https://editorconfig.org/)
- [Dil hizmeti için EditorConfig'i destekleme](../extensibility/supporting-editorconfig.md)
- [Kod düzenleyicisinin özellikleri](writing-code-in-the-code-and-text-editor.md)
