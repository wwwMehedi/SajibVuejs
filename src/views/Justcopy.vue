<div class="col-md-6 pb-3 pl-2 bg-red">
<div class="" v-for="am in amenities" :key="am.id">
              <div v-if="am.id<12">
                 <input class="form-check-input" type="checkbox" :value="am.id" v-model="amen" id="flexCheckDefault" name="amenities[]" data-saving="1">
                   <label class="form-check-label" for="flexCheckDefault">
                     {{am.title}}
                    </label>
              </div>
</div>
</div>