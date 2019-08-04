<script>
  import { onMount, setContext } from "svelte";
  import { navigate } from "svelte-routing";
//   import detail from "./detail.svelte"
  let data=[];
  onMount(async function(){
      let res=await fetch('/data.json');
      let result =await res.json();
      console.log(result)
      data=result;
  })
  let list=[];
 function ShowDetail(item){
  console.log(item)
  list.push(item)
  console.log(list)
 let set =localStorage.setItem('key',JSON.stringify(list))
// navigate('/detail')
  }

</script>

<style>
  .box > img {
    width: 100%;
    height: 100%;
  }
  .list{
    width: 100%;
    height: 100%;
    display: flex;
    flex-wrap: wrap;
    box-sizing: border-box;
    background:#eee;
  }
  .list div{
    flex: 50%;
    text-align: center;
    align-items: center;
    background:#fff;
  }
  .list div dl dd {
    width: 80%;
    margin: 0 auto;
  }
  .list div dl dt img {
    width: 80%;
    height: 100%;
  }

</style>

<div class="box">
  <img
    src="//m.360buyimg.com/mobilecms/s750x366_jfs/t1/31746/32/1528/111163/5c500f8aEe3c6c0e7/0e1519939f544e8d.jpg!cr_1125x549_0_72!q70.jpg.dpg"
    alt="" />
  <div class="list">
{#each data as item,ind(item.name)}
<div>
 <dl>
      <dt>
        <img
          src={item.img}
          alt="" />
      </dt>
      <dd>
        <span>{item.title}</span>
        <p>￥{item.price}</p>
      </dd>
     <button on:click={()=>{ShowDetail(item)}}>加入购物车</button>
    </dl>
    
</div>
{/each}
  </div>

</div>
