# Variables

When a symbolic name is given to a register inside a .plc file and this file is included inside another .plc file using a #funcdec statement, this symbolic will not be included in the scope of the file that has the #funcdec statement. 

For example, let a function block called TEST be defined inside a file called FBTest.plc

<div class="background-plc">
    <div class="comment-plc"> * File: FBTest.plc</div>
    <div class="var-block-plc">
        <div class="vars-plc">VAR </div>
        <div class="var-line"> 
            <span class="var-name">FBTest1</span> 
            <span class="keyword1-control-plc">AT </span>
            <span class="registers-plc">%M255; </span>
        </div>
        <div class="vars-plc">END_VAR </div>
    </div>
    <br />
    <div class="function-block-plc"> 
        <span class="vars-plc">FUNCTION_BLOCK</span>
        <span>TEST</span>
        <div class="var-block-plc"> 
            <span class="vars-plc">VAR_INPUT</span>
            <div class="var-line"> 
                <span class="var-name">xIn: </span> 
                <span class="keyword1-control-plc">DWORD;</span>
            </div>
            <div class="vars-plc">END_VAR</div>
        </div> 
        <br />
        <div class="var-block-plc"> 
            <span class="vars-plc">VAR_OUTPUT</span>
            <div class="var-line"> 
                <span class="var-name">yOut: </span> 
                <span class="keyword1-control-plc">DWORD; </span>
            </div>
            <div class="vars-plc">END_VAR</div>
        </div> 
        <br />
        <div class="var-block-plc"> 
            <span class="vars-plc">VAR</span>
            <div class="var-line"> 
                <span class="var-name">local: </span> 
                <span class="keyword1-control-plc">DWORD; </span>
            </div>
            <div class="vars-plc">END_VAR</div>
        </div> 
        <br />
        <div class="code-plc">
            <div class="var-line"> 
                <span class="keyword1-control-plc">LD</span> 
                <span class="var-name">xIn</span>
            </div>
            <div class="var-line"> 
                <span class="keyword1-control-plc">ST</span> 
                <span class="var-name">yOut</span>
            </div>
        </div>
        <br />
        <span class="vars-plc">END_FUNCTION_BLOCK</span>
    </div> 
</div>
<br />

When this file is included with a #funcdec statement, instances of the TEST function block can be made between VAR-END_VAR but symbolic varibles like FBTest1 are left out of this file's scope so they cannot be used.



<style>
.background-plc {
    background-color: var(--vscode-textCodeBlock-background);
    padding-left: 20px;
    padding-top: 10px;
    padding-bottom: 20px;
}
.comment-plc {
    color: #1aa8bb;
}
.keyword1-control-plc{
    color: #0084ff;
    font-weight: bold;
}
.keyword2-control-plc{
    color: #00ff37;
    font-weight: bold;
}
.vars-plc{
    color: #9900ff;
    margin-right: 10px;
}
.labels-plc{
    color: #00ffea;
}
.comment-plc{
    color: #1aa8bb;
}
.registers-plc{
    color: #ffd000;
}
.numbers-plc{
    color: #ff7700da;
}
</style>
