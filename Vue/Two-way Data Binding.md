- One-way data binding: data -> form properties -> done
- Two-way data binding: data -> form properties -> data 
- v-model: used to create a two-way data binding between properties
```
const member: {
	fname:null;
}
<input type="text" v-model="member.fname" />
```
