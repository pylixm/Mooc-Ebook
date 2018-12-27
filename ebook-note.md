# ����Web�Ķ�������
> vivipure

#1���Ķ�������ԭ����
���ָ�ʽ(txt��pdf��epub��mobi...)�ĵ�����  ==>  ����������(���������ߡ�Ŀ¼�����桢�½�...)  ==>  
(ͨ���Ķ�������)  ==>  ��Ⱦ  ==>  ����(�ֺš�����ɫ��Ŀ¼����ǩ���ʼ�...)

ע
epub��ȫ����Electronic Publication����һ�ֵ��ӳ�����
mobi����Amazon Kindle�ĵ������ʽ

#2����������ͼ��
����һ������[��ַ](https://icomoon.io/app/#/select)
Ȼ�������Ƶ������Ͻ��½�һ��ͼ�꼯��(new empty set),
���ŵ��ͼ�꼯�ϵ�properties�������������޸�(Edit Metadata)������Ϣ
����������ͼ�꼯�ϵ�Import to set����svg�ļ���֮����ѡ��ȫ��(select all)
��������������½ǵ�generate font��֮���ٵ��download

#3������һ��vue-cli��Ŀ
1.ȫ�ְ�װwebpack��vue-cli

2.`vue init webpack Vue-Project`

3.`cd my-project`
 
  `npm install `
  
  `npm run dev` 

#4��ͨ��IP��ַ������Ŀ
�������ն˲鿴������IP��������config�ļ������޸�index.js�ļ���hostΪ0.0.0.0����ô���Ǿ����������ͨ�����ַ�ʽ������
(http://192.168.0.103:8080/#/)

#5����ʽ������Ŀ
- �������鸴�Ƶ�static�ļ�����
- ����sass������npm install node-sass sass-loader --save-dev(���������Ҫ����Ա���)
- �����Ķ�����npm install epubjs --save
- ������ͼ�긴�ƽ������ǵ�css�ļ��е����·����Ҫ����(������Ŀ���ļ�����һ��css�ļ��Լ�һ��fonts�ļ��У�ʹ�÷�������ĳ��Ԫ������Ӷ���õ�����)

#6��rem����
rem��CSS3������һ����Գ��ȵ�λ��rem��ֵ�൱�ڸ�Ԫ��font-sizeֵ�ı���������
1rem = ��Ԫ��font-size
2rem = ��Ԫ��font-size * 2

DOMContentLoaded�¼���̬���ø�Ԫ��font-size
`html.style.fontSize = window.innerWidth / 10 + 'px'`

�ٸ����ӣ���APP.vue������������

```
<script>
export default {
  name: 'App'
}
document.addEventListener('DOMContentLoaded', () => {
  const html = document.querySelector('html')
  let fontSize = window.innerWidth / 10
  fontSize = fontSize > 50 ? 50 : fontSize
  html.style.fontSize = fontSize + 'px'
})
</script>

```

ע������ʼ��HTML�ĵ�����ȫ���غͽ������֮��DOMContentLoaded �¼���������������ȴ���ʽ��ͼ����ӿ�ܵ���ɼ��ء�


#7����һ��pxתrem�ķ���
```
@import 'reset';
// 1rem = fontSize px
// 1px = (1/fontSize)rem
$fonSize: 37.5;
@function px2rem($px) {
  @return ($px / $fonSize) + rem;
}
```

flex���з���

```
@mixin center() {

  display: flex;
  
  justify-content: center;
  
  align-items: center;
}
```


#8��epubjs�ĺ��Ĺ���ԭ�����
epub��ʽ�ĵ����� ==> Book(ͨ��epub.jsʵ������һ��Book����)
Book ==> Rendition(ͨ��renderTo��������һ��Rendition��������������Ⱦ) ==> Theme(������������ʽ������)
Book ==> Location(���������λ�ö�λ)
Book ==> Navigation(����������Ŀ¼�Լ���λ)


#9������eslint�﷨����
��ʽһ��������ڲ����壬��ĳ�����־���Ĺ���ȡ��
```
<script>
/* eslint-disable space-before-function-paren */
export default {
  name: 'Ebook',
  data () {
    return {}
  },
}
</script>
```

����������.eslintrc.js�ļ��н��ù���رյ�(�����Ҫ����npm run dev������Ч)
```
rules: {
    // allow async-await
    'generator-star-spacing': 'off',
    // allow debugger during development
    'no-debugger': process.env.NODE_ENV === 'production' ? 'error' : 'off',
    'space-before-function-paren': 'off'
}
```

#10������flex����
������Զ�������Ԫ���У���flex-grow��flex-shrink��flex-basis���������Ե���д��Ĭ��ֵΪ��0 1 auto����
- flex-grow����������������Ԫ���Լ���������죬����ֵ������Ϊnumber
- flex-shrink���������þ�������Ԫ����ҳ����Сʱ�����α仯������ֵΪnumber��Ĭ��ֵ��1��
��ֵΪ2ʱ��˵��ҳ����Сʱ������Ԫ�ؽ������С��������ֵΪ0ʱ��ҳ����Сʱ������Ԫ�ؿ�Ȳ��ᷢ���ı䡣
- flex-basis�����õ��Ժ�Ԫ�صĳ�ʼ����



#11��һ�ֵ���������ķ���
ͨ��ref�ķ�ʽ���е���
```
<menu-bar :ifTitleAndMenuShow="ifTitleAndMenuShow" ref="menuBar"></menu-bar>
// �˵����͵ײ����������л�
    toggleTitleAndMenu() {
      this.ifTitleAndMenuShow = !this.ifTitleAndMenuShow
      if(!this.ifTitleAndMenuShow) {
        this.$refs.menuBar.hideSetting()
      }
    }
```