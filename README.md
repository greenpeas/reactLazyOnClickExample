# React.lazy() on click example

```
constructor(props) {
    super(props)

    this.state = {
      component: () => { return (<></>) }
    }
  }

  onClickModule = (m) => () => {
    let Module
    switch (m) {
      case 2:
        Module = React.lazy(() => import('./module2/Index.js'))
        break;
      default:
        Module = React.lazy(() => import('./module1/Index.js'))
    }

    this.setState({ component: Module })
  }

  render() {
    return (
      <>
        <button onClick={this.onClickModule(1)}>Module 1</button>
        <button onClick={this.onClickModule(2)}>Module 2</button>
        <Suspense fallback={<div>Loading module...</div>}>
          <this.state.component />
        </Suspense>
      </>
    )
  }
```