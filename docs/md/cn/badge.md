Badge 标记
===

出现在按钮、图标旁的数字或状态标记。


### 基础用法

展示新消息数量。

<!--DemoStart--> 
```js
class Demo extends Component {
  render() {
    return (
      <Badge count={ 12 }>
        <Button size="small">评论</Button>
      </Badge>
    )
  }
}
```
<!--End-->


### 封顶数字

不包裹任何元素即是独立使用，可自定样式展现。

<!--DemoStart--> 
```js
class Demo extends Component {
  render() {
    const {Row,Col} = Layout;
    return (
      <Row gutter="20" style={{width:280}}>
        <Col span="6">
          <Badge count={ 99 }>
            <Button size="small">评论</Button>
          </Badge>
        </Col>
        <Col span="6">
          <Badge count={ 100 }>
            <Button size="small">回复</Button>
          </Badge>
        </Col>
        <Col span="6">
          <Badge count={ 99 } max={10}>
            <Button size="small">点赞</Button>
          </Badge>
        </Col>
        <Col span="6">
          <Badge count={ 1000 } max={999}>
            <Button size="small">打分</Button>
          </Badge>
        </Col>
      </Row>
    )
  }
}
```
<!--End-->

### 独立使用

不包裹任何元素即是独立使用，可自定样式展现。

<!--DemoStart--> 
```js
class Demo extends Component {
  render() {
    const {Row,Col} = Layout;
    return (
      <Row gutter="20" style={{width:150}}>
        <Col span="6">
          <Badge count={25} /> 
        </Col>
        <Col span="6">
          <Badge count={4} style={{ backgroundColor: '#fff', color: '#999', boxShadow: '0 0 0 1px #d9d9d9 inset' }} /> 
        </Col>
        <Col span="6">
          <Badge count={109} style={{ backgroundColor: '#87d068' }} /> 
        </Col>
      </Row>
    )
  }
}
```
<!--End-->

### 小红点

以红点的形式标注需要关注的内容。

<!--DemoStart--> 
```js
class Demo extends Component {
  render() {
    const {Row,Col} = Layout;
    return (
      <Row gutter="20" style={{width:350}}>
        <Col span="6">
          <Badge dot>
            数据查询
          </Badge>
        </Col>
        <Col span="6">
          <Badge dot count={4}>
            <Icon type='message-o' />
          </Badge>
        </Col>
      </Row>
    )
  }
}
```
<!--End-->

### 动态

展示动态变化的效果。

<!--DemoStart--> 
```js
class Demo extends Component {
  constructor(props) {
    super(props);
    this.state = {
      checked: true,
    }
  }
  render() {
    const {Row,Col} = Layout;
    const {checked} = this.state;
    return (
      <Row gutter="20" style={{width:350}}>
        <Col span="6">
          <Badge dot count={checked?1:0}>
            数据查询
          </Badge>
        </Col>
        <Col span="6">
          <Switch 
            checked={this.state.checked}
            onChange={(e,checked)=>{
              this.setState({
                checked:checked
              })
              console.log(`${checked?"选中":'没有选中'}`)
          }}/>
        </Col>
      </Row>
    )
  }
}
```
<!--End-->

## API

### Badge

| 参数 | 说明 | 类型 | 默认值 |
|--------- |-------- |--------- |-------- |
| count | 展示的数字 | Number | - |
| max | 最大值，超过最大值会显示 '{max}+' | Number | `99` |
| dot | 不展示数字，只有一个小红点 | Boolean | `false` |
| status | 设置 Badge 为状态点，展示不同的颜色 | Enum{ 'success', 'processing, 'default', 'error', 'warning' } | - |
| label | 在设置了 status 的前提下有效，设置状态点的文本 | String | - |