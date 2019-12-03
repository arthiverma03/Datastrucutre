
    
import { Component, OnInit, Output, EventEmitter, Input } from '@angular/core';
import { FormGroup, FormControl, Validators } from '@angular/forms';
import { Book } from '../aa';
import {ServiceapiService} from '../api.service'
import { debugOutputAstAsTypeScript } from '@angular/compiler';
import { empty } from 'rxjs';

@Component({
  selector: 'app-book-form',
  templateUrl: './hdpmrg.component.html',
  styleUrls: ['./hdpmrg.component.css']
})
export class BookFormComponent implements OnInit {
 
  
key: any;
apikey: any;
apidata: any;
selectedCountry: String = "--Choose Country--";
  selectedvalue: 0;
  constructor( private api: ServiceapiService) { 
   
  }

  ngOnInit() {
   
    this.api.getSmartphone().subscribe( data => {
      this.key = Object.keys(data);
      

    })
    this.api.getlocalenvurl().subscribe(data => {
      console.log("ssssssssssssss", JSON.stringify(data))
    this.apikey = Object.keys(data)
    this.apidata = data;
    
    })
  }
 

  
  bookcount = [];
  onSelectcity(event){

    let selectedvalue = event.target.value;
  setTimeout(() => {
    if(this.apidata[selectedvalue].hive_db){
      this.bookcount = this.apidata[selectedvalue].hive_db;
    }
    else{
      this.bookcount = [];
    }
   
  }, 0)
    
    
  }
 
}
 









